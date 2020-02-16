### 1.基本概念

​	1.1仓库(Respository)

​		仓库用来存放项目代码，每个项目对应一个仓库，多个开源项目则有多个仓库



### 2. Git工作区域

- ​	工作区(Working Directory)  ：添加、编辑、修改文件等动作

- ​	 Git Repository（Git 仓库）：最终确定的文件保存到仓库，成为一个新的版本，并且对他人可见
- ​     暂存区 ：暂存已经修改的文件最后统一提交到git仓库中

![](https://github.com/tzforevereer/Gallery/blob/master/%E5%9B%BE%E7%89%871.png?raw=true)



### 3.向仓库中添加文件流程

![](https://github.com/tzforevereer/Gallery/blob/master/%E5%9B%BE%E7%89%872.png?raw=true)



### 4. Git上传到github

​		**4.1 基本信息设置**

```
1. 设置用户名
git config --global user.name 'xxxxxxxxxxxxxxxx'

2. 设置用户名邮箱
git config --global user.email 'xxxxxxxxxxxx@qq.com'
```

​		**4.2 向仓库中添加文件**

```
1.在文件内初始化git（创建git仓库）
git init
git add a1.php                       # 添加a1.php到暂存区
git commit -m  '第一次提交文件'    	 # 添加a1.php到仓库
```

​		**4.3 创建SSH KEY**

```
1.先看一下你C盘用户目录下有没有.ssh目录，有的话看下里面有没有id_rsa和id_rsa.pub这两个文件，有就跳到下一步，没有就通过下面命令创建
	
2. $ ssh-keygen -t rsa -C "youremail@example.com"
	 
3. 然后一路回车。这时你就会在用户下的.ssh目录里找到id_rsa和id_rsa.pub这两个文件

4.登录Github,找到右上角的图标，打开点进里面的Settings，再选中里面的SSH and GPG KEYS，点击右上角的New SSH key，然后Title里面随便填，再把刚才id_rsa.pub里面的内容复制到Title下面的Key内容框里面，最后点击Add SSH key，这样就完成了SSH Key的加密。
```

​		**4.4 连接远程仓库**

```
在Github上创建好Git仓库之后我们就可以和本地仓库进行关联了，根据创建好的Git仓库页面的提示，可以在本地仓库的命令行输入：
	$ git remote add origin https://github.com/xxxxxxxx/xxxxx.git
```

​		 注意 ：origin后面加的是你Github上创建好的仓库的地址。

​		**4.5 推送到远程仓库**

```
$ git push -u origin master

由于新建的远程仓库是空的，所以要加上-u这个参数，等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需下面这样就可以了：

$ git push origin master
```

​		**4.6 注意事项**

```
另外，这里有个坑需要注意一下，就是在上面第七步创建远程仓库的时候，如果你勾选了Initialize this repository with a README（就是创建仓库的时候自动给你创建一个README文件），那么到了第九步你将本地仓库内容推送到远程仓库的时候就会报一个failed to push some refs to  https://github.com/xxxxxxxx/xxxxx.git的错。

这是由于你新创建的那个仓库里面的README文件不在本地仓库目录中，这时我们可以通过以下命令先将内容合并以下：

$ git pull --rebase origin master

 这时你再push就能成功了。
```





