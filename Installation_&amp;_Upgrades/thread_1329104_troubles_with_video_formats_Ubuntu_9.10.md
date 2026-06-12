---
title: "troubles with video formats Ubuntu 9.10"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by venom035 on 2009-11-17
I'm trying to uninstall some packages but i keep getting this :
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdvdnav4 libsidplay1 libtwolame0
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 741kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 130352 files and directories currently installed.)
Removing libdvdnav4 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libdvdnav4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing libsidplay1 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libsidplay1 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing libtwolame0 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libtwolame0 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libdvdnav4
 libsidplay1
 libtwolame0
E: Sub-process /usr/bin/dpkg returned an error code (1)

anybody? thx

---

### Post by venom035 on 2009-11-20
I found the solution

it's 
```
apt-get -f install libdvdnav4 libsidplay1 libtwolame0 
```

grtz

---

