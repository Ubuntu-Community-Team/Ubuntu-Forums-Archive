---
title: "can't uninstall yabause-gtk"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by mric on 2010-06-30
Hi Forum

maybe the one or the other stumbled over this situation. i've tried to install yabause with less success, however it is installed and now cant be removed. i do get lesse information and wonder if i can remveo it manually somehow

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 yabause-common libgtkglext1 libmini18n0 freeglut3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  yabause-gtk
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 1,548kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 196807 files and directories currently installed.)
Removing yabause-gtk ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing yabause-gtk (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 yabause-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

