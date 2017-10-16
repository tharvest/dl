# MAC下安装人脸识别的TensorFlow环境 
**本文记录MAC实体环境的安装，非conda，virtualenv，docker等环境**

#### 1.安装pip
pip和easy_install也是python的安装与管理工具，后续都使用pip。
```
$sudo easy_install pip
$sudo easy_install --upgrade six
```
#### 安装TensorFlow
由于[TensorFlow境外网站](https://storage.googleapis.com/tensorflow)访问比较困难，选择[清华大学开源镜像网站](https://mirrors.tuna.tsinghua.edu.cn/help/tensorflow/)，
网站提供了选择：计算单元，操作系统，Python版本，TensorFlow版本的下拉菜单，根据自己的实际环境选择，然后生成安装命令，我的选择如下:

|选项|值|
|:-:|:-:|
|计算单元|CPU|
|操作系统|MAC OS X|
|Python版本|py2|
|TensorFlow版本|1.1.0|

```
$sudo pip install \
  -i https://pypi.tuna.tsinghua.edu.cn/simple/ \
  https://mirrors.tuna.tsinghua.edu.cn/tensorflow/mac/cpu/tensorflow-1.1.0-py2-none-any.whl
```
#### 安装OpenCV
##### 使用homebrew安装
```
$sudo brew install opencv
```
##### 检查OpenCV环境
```
$ python
>>> import cv2 
ImportError: No module named cv2
```
我的环境给出了如下提示：
> Python modules have been installed and Homebrew's site-packages is not
in your Python sys.path, so you will not be able to import the modules
this formula installed. If you plan to develop with these modules,
please run:
  mkdir -p /Users/'yourusername'/.local/lib/python2.7/site-packages
  echo 'import site; site.addsitedir("/usr/local/lib/python2.7/site-packages")' >> /Users/'yourusername'/.local/lib/python2.7/site-packages/homebrew.pth
==> Summary
/usr/local/Cellar/opencv/3.3.0_3: 516 files, 125.0MB

根据提示执行如下命令，将yourusername替换为您自己环境的用户名，重新检查OpenCV，环境OK
```
 $mkdir -p /Users/yourusername/.local/lib/python2.7/site-packages
 $echo 'import site; site.addsitedir("/usr/local/lib/python2.7/site-packages")' >> /Users/yourusername/.local/lib/python2.7/site-packages/homebrew.pth
```
#### 依赖库安装
在执行程序过程中会遇到各种找不到'ImportError: No module named xxx'的问题，当遇到类似问题，可以尝试执行如下命令解决
```
$sudo pip install -i https://pypi.tuna.tsinghua.edu.cn/simple/ xxx
```
这里的xxx表示依赖库的名称

### 参考资料
* [极客学院《TensorFlow 官方文档中文版》- 下载与安装](http://wiki.jikexueyuan.com/project/tensorflow-zh/get_started/os_setup.html)
* [清华大学开源镜像网站-TensorFlow 镜像使用帮助](https://mirrors.tuna.tsinghua.edu.cn/help/tensorflow/)
