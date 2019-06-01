<template>
  <section class="container">
    <div>
      <logo/>
      <h1 class="title">
        nuxt-apollo
      </h1>
      <h2 class="subtitle">
        My peachy Nuxt.js project
      </h2>
      <div>
        <button @click="query">{{message}}</button>
      </div>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green"
        >Documentation</a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >GitHub</a>
      </div>
    </div>
  </section>
</template>

<script>
  import Logo from '~/components/Logo.vue'
  import sample from '~/apollo/sample'

  export default {
    components: {
      Logo
    },
    created() {
      console.log(process.env.ENDPOINT)
    },
    data() {
      return {
        message: "query sample"
      }
    },
    methods: {
      async query() {
        const query = sample;
        const variables = "";
        this.$apollo.query({query, variables})
          .then(({data}) => {
            console.log(data);
          }).catch(data => {
            console.log(data);
        })
      }
    }
  }
</script>

<style>
  /* Sample `apply` at-rules with Tailwind CSS
  .container {
    @apply min-h-screen flex justify-center items-center text-center mx-auto;
  }
  */
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .title {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
  }

  .subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
  }

  .links {
    padding-top: 15px;
  }
</style>
