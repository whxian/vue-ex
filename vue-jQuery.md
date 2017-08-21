# 基于vue-cli搭建的Vue项目引入jQuery #
---

### 1. 安装 在终端输入： ###
```
npm install --save jquery
```

### 2.在webpack.base.conf.js文件中添加 ###
```
function resolve (dir) {
  return path.join(__dirname, '..', dir)
}
module.exports = {
  ... ,
  resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      'vue$': 'vue/dist/vue.esm.js',
      '@': resolve('src'),
      //定义别名和插件位置
      'jquery': resolve('node_modules/jquery/src/jquery')
    }
  }
}
```

### 3.在webpack.prod.conf.js文件中添加 ###
```
plugins: [
  ··· ,
  //全局依赖jQuery
  new webpack.ProvidePlugin({
    $ : "jquery",
    jQuery : "jquery"
  })
```

### 4. 在App.vue中引入JQ ###
```
//引入jQuery
import $ from 'jquery';
```
