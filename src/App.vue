<template>
  <div>
    <app-header></app-header>
    <transition name="fade" mode="out-in">
    <router-view></router-view>
    </transition>
    <app-footer></app-footer>
    </div>
</template>
<script>
import Header from "./components/shared/Header";
import Footer from "./components/shared/Footer";

export default {
  components : {
    appHeader : Header,
    appFooter : Footer,
  },
  created(){
    this.$store.dispatch("getTradeResult");
    this.$store.dispatch("initApp");
  }
} 
</script>
<style>
  .fade-enter{
    opacity: 0;
  }
  .fade-enter-active{
    transition: opacity .3s ease-out;
  }
  .fade-leave{
    /*İçini doldurmamıza gerek yok, sadece leave yollansa yeterli.*/
  }
  .fade-leave-active{
    transition: opacity .3s ease-out;
    opacity: 0;
  }
</style>
