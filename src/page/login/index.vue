
<template>
  <div class="login-container pull-height"
       @keyup.enter.native="handleLogin">
    <div class="login-logo animated fadeIn">
      <img src="/svg/logo.svg"
           alt="">
    </div>
    <div class="login-left animated fadeInLeft">
      <div class="login-info">
        <h2 class="login-info-title">{{website.info.title}}</h2>
        <ul class="login-info-list">
          <li class="login-info-item"
              v-for="(item,index) in website.info.list"
              :key="index">
            <i class="el-icon-check"></i>&nbsp;{{item}}
          </li>
        </ul>
      </div>
    </div>
    <div class="login-border  animated fadeInRight">
      <div class="login-main">
        <h4 class="login-title">登录 {{website.title}}</h4>
        <userLogin v-if="activeName==='user'"></userLogin>
        <codeLogin v-else-if="activeName==='code'"></codeLogin>
        <socialLogin v-else-if="activeName==='third'"></socialLogin>
      </div>
      <div class="login-menu">
        <router-link to="/register">注册</router-link>
        <a href="#"
           @click.stop="activeName='user'">账号密码</a>
        <a href="#"
           @click.stop="activeName='third'">第三方登录</a>
      </div>
    </div>
  </div>
</template>
<script>
import userLogin from './userlogin'
import socialLogin from './sociallogin'
import topTheme from '../index/top/top-theme'
import theme from '@/mixins/theme'
import { mapGetters } from 'vuex'
export default {
  name: 'login',
  mixins: [theme()],
  components: {
    topTheme,
    userLogin,
    socialLogin
  },
  data () {
    return {
      activeName: 'user'
    }
  },
  created () { },
  mounted () { },
  computed: {
    ...mapGetters(['website'])
  },
  props: [],
  methods: {}
}
</script>

<style lang="scss">
.login-container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  // background: rgba(0, 0, 0, 0.2);
  position: relative;
}
.login-container::before {
  z-index: -999;
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-image: url('/img/login.png');
  background-size: cover;
}
.login-left {
  position: relative;
  flex: 1;
}
.login-logo {
  position: absolute;
  top: 0;
  left: 0;
  padding-top: 50px;
  font-size: 24px;
  color: #333;
}
.login-info {
  padding-left: 140px;
}
.login-info-title {
  line-height: 90px;
  color: rgb(52, 58, 64);
}
.login-info-item {
  font-size: 14px;
  line-height: 2.5;
  color: rgb(33, 37, 41);
}
.login-border {
  flex: 1;
  box-sizing: border-box;
}
.login-main {
  margin: 0 auto;
  width: 50%;
  box-sizing: border-box;
}
.login-main > h3 {
  margin-bottom: 20px;
}
.login-main > p {
  color: #76838f;
}
.login-title {
  margin-bottom: 40px;
  font-weight: 500;
  font-size: 22px;
  text-align: center;
  letter-spacing: 4px;
}
.login-menu {
  width: 100%;
  text-align: center;
  a {
    color: rgb(153, 153, 153);
    font-size: 12px;
    margin: 0px 8px;
  }
}
.login-index {
  margin-top: 40px;
  width: 180px;
  height: 48px;
  text-align: center;
  border-radius: 50px;
  background: transparent;
  color: #333;
  font-size: 16px;
  border: 1px solid rgb(152, 22, 244);
}
.login-submit {
  display: block;
  margin: 40px auto 10px auto;
  width: 200px;
  height: 48px;
  font-size: 14px;
  text-align: center;
  border-radius: 50px;
  border: 0px;
  box-shadow: rgba(152, 22, 244, 0.19) 0px 5px 10px 2px;
}
.login-form {
  margin: 10px 0;
  i {

  }
  .el-form-item__content {
    width: 100%;
  }
  .el-form-item {
    margin-bottom: 12px;
  }
  .el-input {
    input {
      padding-bottom: 10px;
      text-indent: 5px;
      background: transparent;
      border: none;
      border-radius: 0;
      color: #333;
      border-bottom: 1px solid rgb(235, 237, 242);
    }
    .el-input__prefix {
      i {
        color: #999;
        padding: 0 5px;
        font-size: 16px !important;
      }
    }
  }
}
.login-code {
  display: flex;
  align-items: center;
  justify-content: space-around;
  margin: 0 0 0 10px;
}
.login-code-img {
  margin-top: 2px;
  width: 100px;
  height: 38px;
  background-color: #fdfdfd;
  border: 1px solid #f0f0f0;
  color: #333;
  font-size: 14px;
  font-weight: bold;
  letter-spacing: 5px;
  line-height: 38px;
  text-indent: 5px;
  text-align: center;
}
</style>
