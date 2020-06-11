@[toc]
GitHub的官方网站为：[GitHub](https://github.com/)
# 一. 什么是GitHub
GitHub是用于版本控制和协作的代码托管平台。它可以让您和其他人在任何地方协同工作，其最基本的操作包括：
（1）创建和使用存储库
（2）启动并管理新分支
（3）对文件进行更改，并将其作为提交推送到GitHub
（4）打开并合并拉取请求

# 二. 注册账户
首先是在官网上注册自己的GitHub账号。
注册完成后进行简单的设置，开始创建一个属于自己的库。

# 三. 创建仓库
   （注意：由于我们是免费用户，因此只能创建公共仓库）

 1. Create a new repository（点击右上角头像旁的"+"，选择"New repository"）
![首先创建一个仓库](https://img-blog.csdnimg.cn/20190919171717975.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_8,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dsaHI2Mg==,size_16,color_FFFFFF,t_70)
（1）"Repository name"是为自己的库起一个库名
（2）"Description"是对自己的库进行一个简单的描述
（3）选择仓库权限为"Public"，即建立公共存储库
（4）可以选择"Initialize this repository with a README"
（5）点击"Create repository"，创建存储库
另外：
gitignore: 不需要进行版本管理的仓库类型，对应生成文件.gitignore
license: 证书类型，对应生成文件LICENSE

 2. 创建完自己的库之后，需要进行本地配置，方便本地代码同步到GitHub所创建的库中。
 
# 四. 安装Git
（以Git Windows版为例，进行Git Bash的安装）
 1. 进入[Git下载页面](https://git-scm.com)，下载适合自己电脑的版本
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190920103111667.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dsaHI2Mg==,size_16,color_FFFFFF,t_70)
下载后的安装包，如下所示：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190920102811322.png)
 2. 下载后双击运行，直接安装，在安装过程中直接默认选项即可。
 3. 若是Linux用户，直接执行如下命令：
```bash
sudo apt-get install git
```

# 五. 配置Git
 1. 运行Git Bash，打开的Git终端如下图所示：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190920104021899.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dsaHI2Mg==,size_16,color_FFFFFF,t_70)
（1）@之前的"rhp62"是你的计算机名
（2）@之后的"LAPTOP-VPJSKCPU"是你的计算机型号

 2. 在本地创建ssh key
 （1）在Git Bash中输入下面的代码，这一步是为了获取属于自己的密钥
 （2）将引号中的your_email@youremail.com改为你在GitHub上注册的邮箱
 ```Bash
ssh-keygen -t rsa -C "your_email@youremail.com"
```
 - 输入上述代码后回车，会要求确认路径和输入密码，我们使用默认一路回车即可 
 - 成功后会在~/下生成.ssh文件夹，进入.ssh文件夹，记事本打开id_rsa.pub，复制里面的key
 
 3. 添加密钥到GitHub上
 （1）打开GitHub的设置界面"Settings"，选择左边的"SSH and GPG keys"选项
 （2）在右上角有一个"New SSH key"，添加新的ssh key
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190920111152416.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dsaHI2Mg==,size_16,color_FFFFFF,t_70)
 （3）"Title"是给自己的密钥起个名字，在"Key"下面填入刚刚复制的id_rsa.pub中的内容
 （4）点击"Add SSH key"，保存即可  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190920114327935.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dsaHI2Mg==,size_16,color_FFFFFF,t_70)
 
 4. 验证是否绑定成功，在Git Bash下输入下列代码
  ```Bash
ssh -T git@github.com
```
 - 如果是第一次进行绑定的话，输入上述代码后会提示是否continue
 - 输入"yes"，如果出现"You've successfully authenticated, but GitHub does not provide shell access"，就表示已经成功连上了GitHub
 5. 执行git config命令，配置用户名和邮箱
  在对本地仓库和GitHub库进行操作之前，还需要设置username和email，因为GitHub每次commit都会对它们进行记录，即通过该配置记录当前版本是由哪个用户提交的，作用仅仅是用于提交代码时的用户标记。
 

```Bash
git config --global user.name "your name"
git config --global user.email "your_email@youremail.com"
```
 - name是GitHub上的用户名
 - email是注册GitHub时使用的邮箱地址
 
# 六. 检出仓库
创建一个本地仓库的克隆版本，执行如下命令

```Bash
git clone /path/to/repository
```
如果是远端服务器上的仓库，执行如下命令

 - 通过ssh

```Bash
git clone username@host:/path/to/repository
```

 - 通过https
```Bash
git clone https:/path/to/repository.git
```
1. 打开Git Bash，定位到本地仓库所在的路径。如果不给Git Bash定位，默认的本地文件位置是在C盘中。
2. 输入命令：git clone https:/path/to/repository.git
git clone后的网址是你创建库成功后的网址
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190920171402580.png)
3. 克隆成功后，会在本地仓库中看到以我的库名所创建的文件夹
# 七. 推送改动
本地仓库由Git维护的三棵"树"组成
第一个是你的工作目录，持有实际文件；
第二个是缓存区（Index），即缓存区域，临时保存你的改动；
第三个是HEAD，指向你最近一次提交后的结果。
1. 打开文件夹，创建或者修改一个任意格式和名称的文件
2. git add test.txt
即计划改动（把它们添加到缓存区）

```Bash
git add <filename>
git add *
```

3. git commit -m "代码提交信息"
即以实际提交改动，此时改动已经提交到了HEAD，但是还未到你的远端仓库

```Bash
git commit -m "代码提交信息"
```

> 【注意】
> 在开发时，良好的习惯是根据工作进度及时进行commit操作。
> 务必注意：附上有意义的 commit message。
> 创建完项目目录后，第一次提交的commit message一般为：「Initial commit」

4. git push origin master
即推送改动，提交到远端仓库
（你也可以将master改成你想要推送的任何分支）

```Bash
git push origin master
```

（1）在输入上述代码后，会出现一个界面让你输入GitHub的账号和密码
（2）输入GitHub的账号密码，点击"Login"
（3）如果出现让你输入GitHub用户名的情况，说明刚刚登录失败，再次输入用户名和密码
（4）推送成功

 - 如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，可以使用如下命令添加：
```Bash
git remote add origin <server>
```
这样就能够将你的改动推送到所添加的服务器上去了。
（1）这里的origin是 < server > 的别名，取什么名字都可以，也可以在push时将 < server > 替换为 origin。但为了以后push方便，我们第一次一般都会先"remote add"。
（2）如果你还没有git仓库，可以在GitHub等代码托管平台上创建一个空（不要自动生成 README.md）的repository，然后将代码push到远端仓库。
 

