---
title: "How to disable cuda and nvidia when install opencv"
date: 2015-06-17
forum: Installation &amp; Upgrades
---

### Post by lee_3 on 2015-06-17
I am using ubuntu 14.04 version 64 bit. I install nvidia driver and cuda before. Now. I want to install opencv  from source file. I don't want to install cuda and nvidia again (as I know opencv have option to ignore it). Could you suggest to me the way to ingore the cuda and nvidia step in configure file of opencv ? Thanks 
As I found, To disable CUDA support in OpenCV, add 
```
-D WITH_CUDA=OFF
```
 to the cmake compilation string used to compile OpenCV. How about nvidia?

---

