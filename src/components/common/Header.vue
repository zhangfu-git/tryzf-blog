<template lang="html">
  <header :class="{ isScrollClass: isScroll }">
    <div class="col-sm-5 hidden-xs">
      <router-link id="logo_a" class="col-sm-5" to="/">
        <img :src="logo" class="logo"/>
      </router-link>
    </div>
    <div class="header-right col-sm-7">
      <Search class="Search"></Search>
      <NavCompoent class="NavCompoent"></NavCompoent>
    </div>
  </header>
</template>

<script>
import NavCompoent from './Nav'
import Search from './Search'
export default {
  data () {
    return {
      logo: '/static/logo.png',
      isScroll: false
    }
  },
  mounted () {
    var vm = this
    window.onscroll = function () {
      vm.changeHeaderPosition(document)
    }
  },
  methods: {
    changeHeaderPosition (document) {
      let top = document.body.scrollTop - 100
      if (top <= 0) {
        this.isScroll = false
      } else {
        this.isScroll = true
      }
    }
  },
  components: {
    NavCompoent,
    Search
  }
}
</script>

<style lang="css" scoped>
  header {
    width:100%;
    position: fixed;
    height:80px;
    line-height: 80px;
    z-index:9999999999;
    top:0;
    transition:all 200ms ease-out;
  }
  .logo {
    width:64px;
    transition:width 200ms ease-out;
    transform-origin: center;
  }
  .isScrollClass {
    background:rgba(255,255,255,0.3);
    box-shadow: 0 1px 2px 0 rgba(0,0,0,0.15);
    top:-10px;
  }
  .isScrollClass .logo {
    width:40px;
  }
  .header-right {
    padding-top:10px;
    text-align: right;
  }
  .Search, .NavCompoent{
    margin-right:30px;
    cursor: pointer;
  }
</style>
