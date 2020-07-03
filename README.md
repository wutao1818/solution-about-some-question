# solution-about-some-question
部分问题的解决方案

1、vue复制的js代码
copy() {
      var copyText = '复制的内容11111111111111';
      var input = document.createElement("input");
      input.value = copyText;
      document.body.appendChild(input);
      input.select();
      input.setSelectionRange(0, input.value.length), document.execCommand('Copy');
      document.body.removeChild(input);
      alert('已复制')
      window.scrollTo(0, 10);
    }

<div @click="copy" id="coppy">复制</div>



2、css文字超过一行省略号
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
word-break: break-all;



3、url带特殊字符的参数，导致ios微信无法识别二维码bug！！！
https://uat-phome.yunqueyi.com/active_news/code?doctorId=123
https://uat-phome.yunqueyi.com/active_news/code?doctorId=123&a=HYD==


4、长按保存图片
img{
   pointer-events:none;/* 禁止长按图片保存 */
}


5、uni-app小程序无法设置页面page的title
// uni本身没有这个方法，但是wx对象有，uni继承了wx，因此可以隐式使用
uni.setNavigationBarTitle({
　　title: 'title文字'
})


6、样式规范：
      H5 移动端：
font-family: "PingFangSC-Regular","-apple-system-font","Source Han Sans","Helvetica Neue","sans-serif";

      PC web端：
font-family: "Helvetica Neue", "Helvetica", "PingFang SC", "Hiragino Sans GB","Microsoft YaHei", "SimSun", "sans-serif";


7、禁止上下滚动出现白色区域
document.body.addEventListener('touchmove', function(e) {
    if(e._isScroller) return;
    // 阻止默认事件
    e.preventDefault();
}, {
    passive: false
});



8、跨域 nginx 反向代理设置
server{
  # 监听9099端口
  listen 9099;
  # 域名是localhost
  server_name localhost;
  #凡是localhost:9099/api这个样子的，都转发到真正的服务端地址http://localhost:9871
  location ^~ /api {
      proxy_pass http://localhost:9871;
  }
}



9、ios 日期转换 NAN 的问题
将日期字符串的格式符号替换成'/'
'yyyy-MM-dd'.replace(/-/g, '/')



10、ios部分机型（6S、X）safari浏览器页面跳转返回后不刷新问题
window.onpageshow = function(event) {
　　if (event.persisted) {
　　　　window.location.reload()
　　}
};

