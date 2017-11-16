### 简单的单页面应用-类似插件库页面：jquery.history.js来监测hash变化，显示不同内容。
### *使用说明 - 由于使用gulp-rev做版本控制需先修改下面对应文件库文件后，执行npm run build 或 npm start
 由于添加了版本号信息，所以需要先手动更改依赖版本号文件：gulp-rev和gulp-rev-collector(重要)
 ``` javascript
 1.打开node_modules\gulp-rev\index.js
    第134行 manifest[originalFile] = revisionedFile;
    更新为: manifest[originalFile] = originalFile + '?v=' + file.revHash;
  2.打开nodemodules\gulp-rev\nodemodules\rev-path\index.js
    10行 return filename + '-' + hash + ext;
    更新为: return filename + ext;
    或者
    9行 return modifyFilename(pth, (filename, ext) => `${filename}-${hash}${ext}`);
    更新为: return modifyFilename(pth, (filename, ext) => `${filename}${ext}`);
  3.打开node_modules\gulp-rev-collector\index.js
    40行 var cleanReplacement =  path.basename(json[key]).replace(new RegExp( opts.revSuffix ), '' );
    更新为: let cleanReplacement =  path.basename(json[key]).split('?')[0];
```
作者：win_wlq
链接：http://www.jianshu.com/p/df593ad8082d
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
## 使用
**需要node环境-npm包**
  执行：安装所需依赖
``` javascript
    npm install
```

**初始化 - 开发环境 - dist**
``` javascript
    npm start
```

**生产环境 - builder**
``` javascript
    npm run build
```
