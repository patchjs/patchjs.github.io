## 核心能力

* 简单易用的 API

* 支持多种存储方式，例如：localStorage、Web SQL Database、IndexedDB

* 通过 Nginx Module 实时计算两个版本之间的 Diff 文件

* 通过 Webpack Plugin 构建生产两个版本之间的 Diff 文件


## 加载器

### 引用文件

```html
<script src="./patchjs-loader/2.0.0/websqldb.js"></script>
<script src="./patchjs-loader/2.0.0/index.js"></script>
```

### API 

```js
patchjs.config({
  path: 'http://static.domain.com/path/to/',
  cache: true,
  increment: true,
  version: '0.1.0'
}).load('index.css').load('common.js').wait().load('index.js', function (url, fromCache) {
  // fromCache 
});
```

[更多](https://github.com/patchjs/patchjs-loader)

### Service Worker

```js
importScripts('./sw-core.js');

sw.config({
  cacheId: 'cachedb',
  precache: [
    './images/test.png',
    'https://gw.alipayobjects.com/zos/rmsportal/CtJlgAZbmyeSCLxqsgqF.png'
  ],
}).run();
```

[更多](https://github.com/patchjs/patchjs-sw)


## Nginx 配置

```bash
location /static/ {
    patchjs on;
    patchjs_max_file_size 1024;
}
```

[更多](https://github.com/patchjs/patchjs-nginx-module)


## Webpack 配置

```js
var PatchjsWebpackPlugin = require('patchjs-webpack-plugin');

module.exports = {
  plugins: [
    new PatchjsWebpackPlugin({
      increment: true,
      path: 'http://static.domain.com/path/to/'
    })
  ]
};
```

[更多](https://github.com/patchjs/patchjs-webpack-plugin)

## 问题反馈

* issue: https://github.com/patchjs/patchjs-loader/issues


