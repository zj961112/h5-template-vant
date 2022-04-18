<template>
  <div id="app">
    <router-view />
  </div>
</template>
<script>
export default {
  name: 'App',
  created(){
    // this.init()
  },
  methods:{
    init(){
      var timestamp = Date.parse(new Date());
      // 企业信息
      wx.config({
          beta: true,
          debug: false,
          appId: 'wwc3e208ce9ec64be3', // 必填，企业微信的corpid，必须与当前登录的企业一致
          agentid: '1000002', // 必填，企业微信的应用id （e.g. 1000247）
          timestamp:timestamp, // 必填，生成签名的时间戳
          nonceStr: '', // 必填，生成签名的随机串
          signature: '',// 必填，签名，见附录-JS-SDK使用权限签名算法
          jsApiList: ['selectExternalContact'], //必填，传入需要使用的接口名称
          success: function(res) {
              // 回调
          },
          fail: function(res) {
              if(res.errMsg.indexOf('function not exist') > -1){
                  alert('版本过低请升级')
              }
          }
      });
    }
  }
}
</script>
<style lang="scss"></style>
