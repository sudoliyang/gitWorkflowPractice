# Git work flow practice


這是一個 Git and Github 的練習項目   
Github 上面這些都是使用一個叫做 markdown 的語法所撰寫基本的文件

## installation & setup 



## Git
Mac 裡頭有內建 git ，需要最新版的話可以使用 [homebrew](http://brew.sh) 安裝  

	brew install git

## Github and SSh 
大部分的 git 都是使用 SSH 連線的方式去同步的，SSH 也是安全性與速度最快的方式 ([延伸閱讀](https://ihower.tw/git/remote.html))  
所以我們必須要建立 SSH Key 與 Github 做安全的通訊。  

	#建立 SSH Key
	ssh-keygen -t rsa -b 4096 -C "your_email@example.com

	#接下來這三個可以直接 enter 跳過，如果需要較高的安全性可以輸入 passphrase。
	Enter file in which to save the key (/Users/liyang/.ssh/id_rsa): 
	Enter passphrase (empty for no passphrase):
	Enter same passphrase again:
如果有多個 ssh key 可以使用 [ssh config](#ssh-config)  
  
  
測試 SSH Key 是否能夠正常與 Github 通訊 
	
	ssh -T git@github.com

	#成功的話會看到 
	Hi sudoliyang! You've successfully authenticated, but GitHub does not provide shell access.

## 基礎概念與指令
Git 可以大致分為 Local (本地) 、與 Repository (儲存庫)  
可以把它看成一個是在本地端的備份區，以及遠端的備份端  
在開始使用 git 之前我們需要初始化  

	mkdir HelloGit
	cd HelloGit
	git init

這時候我們就初始化完成了，開始新增一些資料，並第一次 commit 

	touch README.md 
	git add .
	git commit -am "first commit"

接下來程式只要修改一個段落就可以 commit 一次  
只需要在 commit 一次就會自己儲存，可以用 git log 查看之前提交的紀錄  

	git add .
	git commit -am "commit message"


假設遇到這次的修改改壞了，可以使用 git checkout 去還原  

	git checkout ./                (一次還原全部到最後一次的 commit)
	git checkout README            (只還原特定檔案或是資料夾)






## GUI
安裝 GUI 的 Git，可以依照個人習慣使用
	
	brew cask install sourcetree
	brew cask install github-desktop

##  <span id="ssh-config">SSH Config</span>

在路徑 ~/.ssh/ 建立 config 檔案能夠管理設定何時該使用哪一個 SSH Key  
這樣能夠帶來較清晰的檔案以及 Key 的管理，以下是我的 SSH Config 

	Host github.com
    HostName github.com
    IdentityFile ~/.ssh/github_rsa           (指向到Key的位置)

		

## 延伸閱讀  
[Git flow 開發流程](https://ihower.tw/blog/archives/5140)  
[Git 版本控制系統 by ihower](https://ihower.tw/git/)  
[GIT版本控制  新北市教研中心－程式設計班](https://kingofamani.gitbooks.io/git-teach/content/)
