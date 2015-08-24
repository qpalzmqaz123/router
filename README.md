# router
小型的前端路由

# 用法
具体可以参考sample.html
映入router.js文件之后，首先需要实例化Router对象
```javascript
var router = new Router();
```
然后添加路由地址以及回调函数
```javascript
router.add('index', function() {
	alert('current page: index');
});
```
如果有需要，可以设置首页地址，设置了首页地址之后，如果访问的地址没有添加到路由当中，那么会自动跳回到首页
```javascript
router.setIndex('index');
```
最后，启动它
```javascript
router.start();
```

这样，访问/#!index之后，回调函数会被调用

# 带有参数的情况
```javascript
router.add('search', function(wd, sortType, sortBy) {
	alert('current page: search' + '\nwd: ' + wd + '\nsortType: ' + sortType + '\nsortBy: ' + sortBy);
});
```
对于上述路由，若访问/#!search/word/date/desc, 其中的word,date,desc会分别赋值给回调函数中的wd,sortType,sortBy三个参数

# api
add(addr, callback): 添加路由,注意多次添加同样的addr，则只有最后一次添加的有效
remove(addr): 删除路由
setIndex(index): 设置首页
go(addr): 跳转到某地址, 如go('index/page/100');
reload(): 重新载入，会根据当前地址重新调用回调函数
start(): 提供此函数是为了即使直接访问路由地址仍然能成功调用回调函数
