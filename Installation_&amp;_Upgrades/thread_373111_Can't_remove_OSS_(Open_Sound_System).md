---
title: "Can't remove OSS (Open Sound System)"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by kylepe on 2007-02-28
I have XUbuntu (I'm new to Linux). I need to remove Open Sound System and then install it properly, but if I attempt to install anything I get the message: **"E: The package oss-linux needs to be reinstalled, but I can't find an archive for it."** (even though the .deb package is on the desktop). So I tried this command: **"sudo dpkg --remove --force-depends --force-remove-reinstreq oss-linux"** as per this thread: **[http://ubuntuforums.org/showthread.php?t=348603](http://ubuntuforums.org/showthread.php?t=348603)**

but I get this message:

kyle@ubuntu-ck:~$ sudo dpkg --remove --force-depends --force-remove-reinstreq oss-linux
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 111146 files and directories currently installed.)
Removing oss-linux ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux (--remove):
 subprocess pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.17-11-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux


Any help very much appreciated! -THX

---

### Post by kylepe on 2007-03-01
I'm thinking the time it's going to take to figure out the problem and fix it may take longer than to actually re-install XUbuntu (due to my lack of experience). So if no response by the weekend I'll proceed with the reinstall (don't strain yourself trying to figure it out). I must have messed up linux real good, I can't even do any updates.

-L8R

---

### Post by debaseme on 2007-03-01
hey man.. had same prob
go to this thread- [http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

oh also.. you might wanna dl the .deb package if you already haven't
here - [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

hope this helps
-peace

---

