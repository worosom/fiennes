<template>
  <div id="app">
    <p v-for="(str, i) in strings"
       :key="i"
       @mouseover="say(str)"
       @touchdown="say(str)">
    {{str}}
    </p>
  </div>
</template>
<script>
import strings from './content/strings'

export default {
  name: 'app',
  components: {
  },
  data() {
    return {
      strings
    }
  },
  mounted() {
    this.synth = window.speechSynthesis
  },
  methods: {
    say(utterance) {
      this.synth.cancel()
      const utterThis = new SpeechSynthesisUtterance(utterance);
      this.synth.speak(utterThis)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Calibri', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  font-size: 100%;
  column-count: 1;
  column-gap: 1rem;
}

@media (min-width: 140px) {
  #app {
    column-count: 2;
  }
}

@media (min-width: 280px) {
  #app {
    column-count: 3;
  }
}

@media (min-width: 375px) {
  #app {
    column-count: 4;
  }
}

@media (min-width: 700px) {
  #app {
    column-count: 5;
  }
}

@media (min-width: 1024px) {
  #app {
    column-count: 6;
  }
}

@media (min-width: 1280px) {
  #app {
    column-count: 7;
  }
}

#app p {
  margin: 0;
  overflow: hidden;
  white-space: nowrap;
}
</style>
