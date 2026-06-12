---
title: "After installing updates on 9/22/14, GUI is frozen (NVIDIA error)"
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by mreider2 on 2014-09-22
im a relative newb to ubuntu/linux, running 14.04, installed latest security updates (about 200mb worth), rebooted the laptop

after kernel boot its stuck on login screen, i can see the mouse pointer but nothing else. 

running cmd (cntrl+alt+F1), then running startx (black screen, nothing happens), getting this error,

Loading extension GLX
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_331'
modprobe: ERROR: could not insert 'nvidia_331':Function not implemented

something in latest update screwed up the display drivers

---

### Post by mreider2 on 2014-09-22
uninstalled all nvida drivers, ran apt-get nvidia-current but same issue, 

found this and this helped, got the screen back (still seeing some bugs but much better now than before)

**Remove everything to do with the Nvidia proprietary drivers.**


[LIST=1]
[*]sudo nvidia-settings --uninstall
[*]sudo apt-get remove --purge nvidia*
[/LIST]
**Start from scratch.**


[LIST=1]
[*]sudo apt-get remove --purge xserver-xorg-video-nouveau xserver-xorg-video-nv
[/LIST]
**Reinstall all the things!**


[LIST=1]
[*]sudo apt-get install nvidia-common
[*]sudo apt-get install xserver-xorg-video-nouveau
[*]apt-get install xserver-xorg
[*]sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
[/LIST]
**Reconfigure the X server.**


[LIST=1]
[*]sudo dpkg-reconfigure xserver-xorg
[/LIST]

---

### Post by mreider2 on 2014-09-26
still getting screen freeze, 

heres the exact bug,

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1210077](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1210077)

---

### Post by mreider2 on 2014-09-29
figured out a workaround

my env is Dell Latitude E6530 laptop with Ubuntu 14.04 x64 with Nvidia drivers (GF108GLM)

the issue was, I was using X.Org X server display driver, if you close the laptop lid and put it to sleep, when waking it up the screen freezes, cant VT or do anything except for hard reboot.

to fix this, go to Software & Updates, click additional drivers tab, choose "Using NVIDIA binary driver version 331.38 from nvidia-331-updates (or whatever the latest ver is), click APply changes

now heres the important part, sudo as root and reboot the box, if you dont reboot the changes dont take effect. Once rebooted i have no issues (as of yet) with my display when waking up.

---

