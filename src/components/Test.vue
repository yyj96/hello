<template>

<el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
    <el-form-item label="用户名" prop="userName">
        <el-input v-model="ruleForm.userName"></el-input>
    </el-form-item>
    <el-form-item label="密码" prop="passWord">
        <el-input type="password" v-model="ruleForm.passWord" auto-complete="off"></el-input>
    </el-form-item>
    <!-- <el-form-item label="确认密码" prop="checkPass">
        <el-input type="password" v-model="ruleForm.checkPass" auto-complete="off"></el-input>
    </el-form-item> -->

    <el-form-item>
        <el-button type="primary" @click="submitForm('ruleForm')">登录</el-button>
        <!-- <el-button type="primary" @click="submitForm('ruleForm')">注册</el-button> -->
        <el-button @click="resetForm('ruleForm')">重置</el-button>
  </el-form-item>
</el-form>


</template>

<script>
export default {
    name: 'Test',
    data() {
      return {
        ruleForm: {
          userName: 'aa',
          passWord: ''   
        },
        rules: {
          userName: [
            { required: true, message: '请输入用户名', trigger: 'blur' },
            { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
          ],
          passWord: [
            { required: true, message: '请输入', trigger: 'blur' },
            { min: 6,  message: '长度在 6 个字符以上', trigger: 'blur' }
          ]
        }
          
      }
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            // alert('submit!');
            // console.log(this.ruleForm)
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }

}
</script>

<style>
.demo-ruleForm{
  width:400px;
  margin:0 auto;
}

</style>


