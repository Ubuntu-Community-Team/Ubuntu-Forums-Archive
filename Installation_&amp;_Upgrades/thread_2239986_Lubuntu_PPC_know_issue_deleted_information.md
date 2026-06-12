---
title: "Lubuntu PPC know issue deleted information"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by estrella-ed on 2014-08-17
Hello  ):P, thanks for reading me, I have a problem with lubuntu 14.04 on a mac power pc g4, after finishing with the installation of the system on the first boot attempt an error appears. The Whole screen is black, unless the little white arrow of the mouse, i try to fix the problem by reconfiguring xorg.conf but cannot achieve this :mad:. In the official lubuntu wiki section some one explain the steps to solve the problem, but the information is incomplete, the supposed new xorg configuration file is no more on pastebin. So i really dont know how to fix this. Please if someone can reupload that file would be great. Thanks.  :p

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC)


This is the missing file


[http://paste.ubuntu.com/1284325/plain/](http://paste.ubuntu.com/1284325/plain/)


So this will not work at all. 

sudo wget [http://paste.ubuntu.com/1284325/plain/](http://paste.ubuntu.com/1284325/plain/) -O /etc/X11/xorg.conf

---

### Post by estrella-ed on 2014-10-09
Ok, so, after trying several linux distro for powerpc, the only one who really work 100% with no audio or video error is ubuntu 12.04 and derivatives like kubuntu xubuntu and lubuntu.
New kernels on new distros version like ubuntu 14.04 or ubuntu 14.10 doesn't have the correct audio modules. 
Another annoying problem is  black screen after fresh installation. You can pass those error by typing in yaboot prompt:
Linux video=radeonfb:1024x768-32@60 (replace 1024x768 for your native resolution, 32 is color bit depth and @60 is the refrashe rate).
Fb video drivers not good for playing videos so you will have to find  the correct video driver and Xorg configuration to optimize video playback. 
I try some fixes and workaround for audio issues, but nothing seems to work. And recompiling the kernel is not an option for me. 
Lubuntu 12.04 is my only recommended distro por powerpc. 
And debian squeeze work 100% no error after fresh install. But maybe too old. 
Debian testing have the same problems as ubuntu 14.04 and 14.10. 

Now i have some yaboot error but that is another story. 

The End.

---

