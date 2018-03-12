<template>
  <div id="todo-list">
    <input v-model="todoText" placeholder="Input TODO"/>
    <button @click="add()" v-attr="disabled:!todoText">Add</button>
    <button @click="removeAll()">Remove all</button>

    <div v-repeat="items">
      <span @click="done=!done" v-style="text-decoration:done?'line-through':''">{{$index}} - {{text}}</span>
      <button @click="remove()">Remove</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  data: {
    items: [],
    todoText: ''
  },
  methods: {
    add: () => {
      this.items.push({text: this.todoText})
      this.todoText = ''
    },
    remove: (ev) => {
      this.items.remove(ev.targetVM.$data)
    },
    removeAll: () => {
      // #e = this.items
      // #pop = e.pop.bind e
      // #[0 to e.length].forEach pop
      this.items = []

    }
  }
}
</script>

<style scoped>

</style>
