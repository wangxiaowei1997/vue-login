<template>
  <div>
    <div class="outer_label">
      <img class="inner_label login_logo" src="../assets/logo.png">
    </div>
    <div class="login_form">
      <el-input  prefix-icon="el-icon-user" type="text" class="cc" placeholder="用户名" v-model="userName"></el-input>
      <el-input  prefix-icon="el-icon-key" type="text" class="cc" placeholder="密码" v-model="password"></el-input>
      <!--<button class="login_btn el-button el-button&#45;&#45;primary is-round" type="primary" round>登录</button>-->
      <el-button class="login_btn" @click.native="login" type="primary" round :loading="isBtnLoading">登录</el-button>
      <div style="margin-top: 10px">
        <span style="color: #000099;" @click="login">司机账号登陆</span>
        <span style="float: right;color: #A9A9AB">忘记密码？</span>
      </div>
    </div>
  </div>
</template>

<script>
//  import { userLogin } from '../../api/api';

export default {
  data () {
    return {
      userName: '',
      password: '',
      isBtnLoading: false
    }
  },
  created () {
    if (JSON.parse(localStorage.getItem('user')) && JSON.parse(localStorage.getItem('user')).userName) {
      this.userName = JSON.parse(localStorage.getItem('user')).userName
      this.password = JSON.parse(localStorage.getItem('user')).password
    }
  },
  computed: {
    btnText () {
      if (this.isBtnLoading) return '登录中...'
      return '登录'
    }
  },
  methods: {
    login () {
      if (!this.userName) {
        this.$message.error('请输入用户名')
        return
      }
      if (!this.password) {
        this.$message.error('请输入密码')
      }
    }
  }
}
</script>
<style>
  .login_form {
    padding-top: 5%;
    padding-left: 10%;
    padding-right: 10%;
  }

  .qxs-ic_user {
    background: url("../assets/login/ic_user.png") no-repeat;
    background-size: 13px 15px;
    background-position: 3%;
  }

  .qxs-ic_password {
    background: url("../assets/login/ic_user.png") no-repeat;
    background-size: 13px 15px;
    background-position: 3%;
    margin-bottom: 20px;
  }

  .login_logo {
    height: 100%;
  }

  .login_btn {
    margin: 20px;
    margin-left: 10%;
    width: 30%;
    font-size: 16px;
    background: -webkit-linear-gradient(left, #000099, rgba(33, 84, 250, 0)); /* Safari 5.1 - 6.0 */
    background: -o-linear-gradient(right, #000099, #2154FA); /* Opera 11.1 - 12.0 */
    background: -moz-linear-gradient(right, #000099, #2154FA); /* Firefox 3.6 - 15 */
    background: linear-gradient(to right, rgba(65, 179, 250, 0.6), rgb(69, 44, 250)); /* 标准的语法 */
    filter: brightness(1.4);
  }
</style>
