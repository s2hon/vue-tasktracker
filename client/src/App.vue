<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
    <AddTask @add-task="add" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/Add.vue'


export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    //function that returns object
    return {
      tasks: []
    }
  },
  methods: {
    add(task) {
      this.tasks = [...this.tasks, newTask]
    },
    deleteTask(id) {
      if(confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    }
  },
  created() {
    //life cycle method-a component is loaded a function is fired off (hooks)
    //http request, load data when component loads
    this.tasks = [
      {
        id: 1,
        text: 'Doctors appt',
        day: 'Mar 17th @ 5PM',
        reminder: true

      },
    ]
  }
}


</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: 'Poppins', sans-serif;
  }
  .container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
  }
  .btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
  }
  .btn:focus {
    outline: none;
  }
  .btn:active {
    transform: scale(0.98);
  }
  .btn-block {
    display: block;
    width: 100%;
  }
</style>