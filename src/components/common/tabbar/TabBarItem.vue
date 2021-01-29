<template>
<div class="tab-bar-item" @click="itemClick">
  <div v-if="!Isactive"><slot  name="item-icon"></slot></div>
  <div v-else><slot  name="item-icon-active"></slot></div>
  <div :style="activestyle"><slot  name="item-text"></slot></div>
<!--  <img src="../../assets/img/tabbar/首页.png" alt="">
  <div>首页</div>-->
</div>
</template>
<script>
    export default {
        name: "TabBarItem",
      props:{
           path:String,
           activeColor:{
             type:String,
             default:'red'
           }

      },
      computed:{
            Isactive(){
              return this.$route.path.indexOf(this.path)!==-1
            },
        activestyle(){
              return this.Isactive ? {color:this.activeColor} : {}
        }
      },
      methods:{
      itemClick() {
             this.$router.replace(this.path)
         }
      }
    }
</script>

<style scoped>
  .tab-bar-item{
    flex:1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }
  .tab-bar-item img{
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
    margin-bottom: 2px;
  }

</style>
