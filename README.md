# 記錄下折騰青龍面板的過程
## 項目一 Dailycheckin
在安裝依賴過程中發現部分依賴無法安裝，上git找到issue下的解決方法
> @lupohan44 ：需要额外apk add libffi libffi-dev openssl openssl-dev

遂嘗試重新進行部署更新（2021-12-4）--部署成功，感謝大佬  
完整命令如下：

```
apk add --no-cache --virtual .build-deps gcc musl-dev python2-dev python3-dev
apk add libffi libffi-dev openssl openssl-dev
pip3 install pip setuptools --upgrade
pip3 install cryptography~=3.2.1
```
## 項目二 簽到盒（Dailyck的上游）
這個比較簡單，直接repo大佬的代碼就行
```
ql repo https://github.com/Wenmoux/checkbox.git "index|install" "node_modules|icon" "scripts|config|Template|sendmsg"
```
> 1 首先在青龙目录下config.sh设置里拉取sh后缀文件 大概这个自己找RepoFileExtensions="js py sh"  
2 在面板内添加定时任务 (上面ql repo那条 定时看你)  
3 手动运行签到盒安装任务 成功后请禁用  
4 在ql/config/config.yml里填写cookie以及需要运行的任务列表(开头cbList)等信息  

就這樣，完畢！
