---
title: "[Ubuntu] Root will not mount after Upgrade"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2013-03-16
I upgraded my 10.04 LTS Server to 12.04 after the upgrade the root filesystem will not mount properly. It is part of a raid array with lvm and a reiser file system.  I get an error messages that the disk is damaged but If I boot a rescue disk and run fsck on it it checks out clean.

on boot I get and error 

"disk drive for / not ready or not present"

If I drop in the recover shell I get and error 

"root filesystem check failed"

The root filesystem is mounted read only and other file systems are not mounted.

---

### Post by rsteinmetz70112 on 2013-03-17
I've solved it.

In the recovery shell
[INDENT]# mount -0 remount, rw /
# mount -a[/INDENT]
Check to see that everything is mounted correctly. There is a tendancy to create nee MD devices and give them numbers beginning with 127.
[INDENT]# dpkg --configure -a
# reboot[/INDENT]
I could boot. I still had a few dependencies to clean up.

---

