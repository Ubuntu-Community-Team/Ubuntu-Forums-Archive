---
title: "FATAL: Could not open '/boot/System.map-player': No such file or directory"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by boulderjams on 2007-02-16
So after upgrading to Feisty, everything went just fine. Not after running the update manager, all updates go just fine and then I get this message. I have tried to apt-get remove, dpkg -r, etc etc. Any ideas?

```

schatz@schatz-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-player-kernel-modules-2.6.20-8 (2.6.20.2-8.6) ...
FATAL: Could not open '/boot/System.map-player': No such file or directory
dpkg: error processing vmware-player-kernel-modules-2.6.20-8 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player-kernel-modules-2.6.20-8
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by yanns on 2007-02-17
Same problem here.

---

### Post by yanns on 2007-02-22
I resolve this problem by copying /boot/System.map.xxxx (xxxx descibring a file that exist) into the missing file.

---

