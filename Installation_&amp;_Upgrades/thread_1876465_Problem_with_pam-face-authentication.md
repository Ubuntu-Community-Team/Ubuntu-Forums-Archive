---
title: "Problem with pam-face-authentication"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by und3rw0rld on 2011-11-06
Hello, I have a problem with my pam-face-authentication. I hope someone could help me to resolve this problem:

**What steps will reproduce the problem?**
1. I installed pam-face-authentication-0.3 
2. When i run qt-face trainer the program star and when i clic on the Start button i get this error in terminal ```

mmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
Unable to stop the stream.: Bad file descriptor
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
``` and after that when i hit capture, my qt-facetreiner crash and i'm getting an error:```
OpenCV Error: Bad flag (parameter or structure field) (Unrecognized or unsupported array type) in cvGetMat, file /build/buildd/opencv-2.1.0/src/cxcore/cxarray.cpp, line 2476
Qt has caught an exception thrown from an event handler. Throwing
exceptions from an event handler is not supported in Qt. You must
reimplement QApplication::notify() and catch all exceptions there.

terminate called after throwing an instance of 'cv::Exception'
  what():  /build/buildd/opencv-2.1.0/src/cxcore/cxarray.cpp:2476: error: (-206) Unrecognized or unsupported array type in function cvGetMat

Aborted
```


**What is the expected output? What do you see instead?**
When i hit capture my face should be scaned, instead it crash and i get  
this error:

```
root@shadow-notebook:~# qt-facetrainer 
mmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
Unable to stop the stream.: Bad file descriptor
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
OpenCV Error: Bad flag (parameter or structure field) (Unrecognized or unsupported array type) in cvGetMat, file /build/buildd/opencv-2.1.0/src/cxcore/cxarray.cpp, line 2476
Qt has caught an exception thrown from an event handler. Throwing
exceptions from an event handler is not supported in Qt. You must
reimplement QApplication::notify() and catch all exceptions there.

terminate called after throwing an instance of 'cv::Exception'
  what():  /build/buildd/opencv-2.1.0/src/cxcore/cxarray.cpp:2476: error: (-206) Unrecognized or unsupported array type in function cvGetMat

Aborted
root@shadow-notebook:~#

```


What version of the product are you using? On what operating system?

pam-face-authentication-0.3.tar.gz Version 0.3 Mace Filter and LBP for Verification - Gsoc 2009 , Ui in qt , (updated) Build 3

I'm using Ubuntu 11.10 Oneiric Ocelot

---

### Post by Enigmapond on 2011-11-06
You really should have read the forum prior to installing this bad piece of code. This does not work properly and can actually damage the system. The only solution I found after many requests for help here was to re-install. My suggestion is to backup important files and re-install. It did't work in 9.04 or 10.04. Good Luck.

---

