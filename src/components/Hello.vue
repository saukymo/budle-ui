<template>
  <div class="hello">
    <div class="nav">
      <div class="nav-left">
        <a class="nav-item">
          <img src="http://localhost:8000/static/favicon.ico" alt="Budle logo">
        </a>
      </div>

        <div class="nav-center">
          <a class="nav-item">
            <span class="icon">
              <i class="fa fa-github"></i>
            </span>
          </a>
          <a class="nav-item">
            <span class="icon">
              <i class="fa fa-twitter"></i>
            </span>
          </a>
        </div>
        <div class="nav-right nav-menu">
          <a class="nav-item">
            Home
          </a>
          <a class="nav-item">
            Documentation
          </a>
          <a class="nav-item">
            Blog
          </a>
        </div>
    </div>

    <ul id='keyboard-list'>
      <li v-for="item in keyboards">
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      keyboards: []
    }
  },
  methods: {
    foo: function () {
      console.log('foo')
    },
    getKeyboards: async function () {
      var response = await this.$http.get('http://localhost:8000/sample_list')
      console.log(1)
      this.keyboards = response.body
    }
  },
  mounted: function () {
    console.log('ready')
    this.foo()
    this.getKeyboards()
  }
}
</script>

<style lang="scss">
@import '~bulma/sass/utilities/variables';
@import '~bulma/sass/utilities/mixins';

</style>
