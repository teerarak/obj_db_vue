<template>
  <div id="app">
  <ol>
    <li v-for="(todo, index) in todos">
      <input v-if="todo.edit" type="text" v-model="todo.text">
      <span v-else>{{ todo.text }}</span>

      <button v-if="!todo.edit" @click="edit(index)">edit</button>
      <button v-else @click="save(index)">save</button>

      <button @click="remove(index)">x</button>
    </li>
  </ol>
  <form @submit.prevent="addTodo">
    <input type="text" v-model="newTodo">
    <input type="submit">
  </form>
</div>
</template>

<script>
import Hello from './components/Hello'

export default {
  name: 'app',
  data () {
    return {
      newTodo: '',
      todos: [{
        text: 'fluke',
        edit: false
      }, {
        text: 'fern',
        edit: false
      }]
    }
  },
  components: {
    Hello
  },
  methods: {
    addTodo () {
      this.todos.push({
        text: this.newTodo,
        edit: false
      })
      this.newTodo = ''
    },
    remove (index) {
      this.todos.splice(index, 1)
    },
    edit (index) {
      this.todos[index].edit = true
    },
    save (index) {
      this.todos[index].edit = false
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
