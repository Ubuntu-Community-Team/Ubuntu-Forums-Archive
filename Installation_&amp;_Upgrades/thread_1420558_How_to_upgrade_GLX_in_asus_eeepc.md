---
title: "How to upgrade GLX in asus eeepc??"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by miousername on 2010-03-03
Hi, i've a asus eeepc with an Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) with Karmic Koala, my GLX version is 1.2 , is it possible to upgrade in some way to GLX 1.3??

Thanks for your reply!

---

### Post by yogesh.girikumar on 2010-03-04
Hi,

A particular version can be forced using the following command. 
```
$ sudo apt-get install <package>=<version>
```
So in your case, you can try this:
```
$ sudo apt-get install nvidia-xgl=1.3
```
Try uninstalling an earlier version to avoid version conflicts..

I'm curious why you wan't to upgrade it if you already have the default version..

Hope this helps.

---

### Post by miousername on 2010-03-04
Hi yogesh.girikumar :),
thank you for your reply, i want update my GLX from version 1.2 to 1.3 because i use some programs that need GLX 1.3 :) if i don't use GLX 1.3 i've an indirect rendering ... i would try your suggestion but is it possible use nvidia-glx on intel graphics card? :confused:

---

### Post by yogesh.girikumar on 2010-03-05
Hi,

Intel cards work best with Intel graphics drivers for linux. You can install the latest drivers by doing : 
```
# sudo nvidia-settings --uninstall
# sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
# sudo dpkg-reconfigure xserver-xorg
```
I'm not sure if upgrading to a newer nvidia driver gives direct rendering capability. To find out if you have direct rendering enabled, you can do:
```
$ glxinfo | grep -i "direct rendering" 
```
To test 3D graphics ( no of frames per second supported ) do:
```
$ glxgears
```
This should show 3D rotating gears and the number of frames every 5 seconds. If nothing is wrong with the gears, you're fine.

Also do:
```
LIBGL_DEBUG=verbose glxinfo
```
If you don't see any errors or segmentation fault, everything is working normally.

See: [http://www.intel.com/support/graphics/sb/CS-010512.htm](http://www.intel.com/support/graphics/sb/CS-010512.htm)
Also: [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

HTH

---

