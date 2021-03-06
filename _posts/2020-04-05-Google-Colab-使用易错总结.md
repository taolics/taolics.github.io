---
title: Google Colab 使用易错总结
author: Tour
date: 2020-04-05 10:44:00 +0800
categories: [工具]
tags: [Google]
math: true
mermaid: true
---

**<center>Google Colab 使用易错总结</center>**  
## 正常步骤  
[以SiamFC++为例](https://blog.csdn.net/qq_30347421/article/details/104534297)  

## 注意点   
### 1.一定要注意先选取运行环境！！！否则后面的工作白做   
### 2.在colab中使用命令需要注意对空格的转义  
```
!python /content/drive/My\ Drive/BertNer/BERT_NER.py 
```
### 3.colab运行目录是/content/drive/My Drive  
要特别注意当前工作目录，使用以下命令进入当前目录

```
%cd /content/gdrive/My\ Drive/yourfilename
```
### 4.如何在colab上更改tensorflow版本  
查看当前版本  

```
!pip3 show tensorflow
```
方法一：如果想将2.x版本（目前colab默认2.x）改成1.x （这种方式只能在1.x和2.x之间转换）  
```
%tensorflow_version 1.x
import tensorflow as tf
tf.__version__
```
方法二：同本地命令行
```
!pip uninstall tensorflow
!pip install tensorflow==1.11
```
注意：上面两种方法使用完成后，都要重启runtime，命令如下：
```
import os
os.kill(os.getpid(), 9)
```
### 5.colab不能自己新建文件夹，所以保存成文件输出路径要注意去掉文件夹

```
#out = cv2.VideoWriter('./output/'+args["input"][43:57]+ "_" + args["class"] + '_output.avi', fourcc, 15, (w, h))

out = cv2.VideoWriter('./'+args["input"][43:57]+ "_" + args["class"] + '_output.avi', fourcc, 15, (w, h))
```
### 6.Cannot connect to X server GOOGLE COLAB怎么办？  
[Cannot connect to X server GOOGLE COLAB](https://stackoverflow.com/questions/54577083/cannot-connect-to-x-server-google-colab)  
简而言之：注释掉所有输出（如cv.imshow等），转为保存成文件  

## 其它易错点总结  
https://zhuanlan.zhihu.com/p/98210226  
https://www.jianshu.com/p/a42d69568966  
https://zhuanlan.zhihu.com/p/105647700
https://zhuanlan.zhihu.com/p/89311070?utm_source=wechat_session   

  

### 如有错误欢迎指出（本文档持续更新）