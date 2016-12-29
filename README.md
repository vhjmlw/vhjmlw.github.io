## 建磊的博客
#####当前博客使用Hexo搭建，主题使用的apollo，简约大方
#####但是apollo主题对于GitHub Flavour MarkDown语法的支持并不完善，有些语法解析错误，如：将图片链接解析为纯图片，复选框语法无法解析。
#####鉴于Hexo + GitHub Pages搭建个人博客的教程网上已经有很多了，这里就不再描述搭建过程
#####博客访问地址：https://vhjmlw.github.io 或 http://www.jianlei.info   

###在博客项目根目录中添加README.md文件  

source目录中的内容相当于源代码文件，里面的内容都会被转换为public目录中的文件。放在source根目录中的文件`hexo generate`之后都会被转换到public根目录中，如favicon.ico、CNAME。   

`hexo deploy` 时会完全拷贝 public 下的文件到 ***.deploy_git*** 下，同时删除多余的文件，所以提前将 README 放到 ***.deploy_git*** 下是不行的。而执行 `hexo generate` 时，public 文件夹下的文件会被完全更新，同样会删除多余文件，所以也不能提前放在 public 下。理论上应该放在 source 文件夹里，但是 .md 文件会被渲染成 html 文件，所以也不行。而在 `hexo generate` 之后将 README 拷贝到 public 下则是一个可行的方法。   

操作步骤如下：  
1. 在微博项目的根目录下新建一个README.bak文件，以备拷贝到public根目录下  
2. 在项目的根目录下新建一个文件如`deploy`（文件名可以自定义)，在`deploy`文件中添加内容：
```
hexo clean
hexo generate
echo Copy README.md
cp ./README.bak ./public/README.md
hexo deploy
```
以上内容包含了四条指令：`hexo clean`、`hexo generate`、`cp README文件`、`hexo deploy`   
> 四条指令的说明：  
> 1. hexo clean  
> 2. hexo generate  
> 3. 将项目根目录中的README.bak文件拷贝到public根目录中，并重命名为README.md  
> 4. hexo deploy  

3. `source deploy`部署博客  

   deploy文件中包含了四条指令，执行deploy文件就相当于按照先后顺序依次执行这四条指令。以后在部署博客的时候可以直接执行一条指令：`source deploy`，就相当于按照先后顺序依次执行这四条指令。  

   当然，也可以按照需求将这四条指令拆分组合。  

#####关于在博客项目根目录下添加README.md文件，可以参考链接：http://jalonwong.github.io/2015/07/12/hexo-readme