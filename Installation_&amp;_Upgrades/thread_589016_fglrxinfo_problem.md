---
title: "fglrxinfo problem"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by abds on 2007-10-23
Hello

I upgraded to gutsy and was having driver problems. I manually installed the driver from [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually).

Everything seems to be working fine. Except when i try to do "fglrxinfo" or "glxgears" I get the following error: 

glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory.


Any help would be appreciated. 

Thanks a lot!

---

### Post by drachenstern on 2007-10-24
Sounds like you didn't possibly try every step of that walkthrough.  I went step by step (3 reboots for crying out loud) and all of that worked fine.

BTW, after finishing all of that wiki, Synaptic install xserver-xgl

---

