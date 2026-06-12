---
title: "Can't remove resin and resin pro"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by steven13690 on 2011-10-10
I tried removing resin pro which i installed using aptitude a few months ago. but i get message:

sudo apt-get remove resin-pro

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  resin-pro
0 upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 357214 files and directories currently installed.)
Removing resin-pro ...
 Removing any system startup links for /etc/init.d/resin ...
   /etc/rc0.d/K10resin
   /etc/rc1.d/K10resin
   /etc/rc2.d/S90resin
   /etc/rc3.d/S90resin
   /etc/rc4.d/S90resin
   /etc/rc5.d/S90resin
   /etc/rc6.d/K10resin
/usr/sbin/invoke-rc.d: 446: /etc/init.d/resin: not found
invoke-rc.d: initscript resin, action "stop" failed.
dpkg: error processing resin-pro (--remove):
 subprocess installed pre-removal script returned error exit status 127
/usr/sbin/invoke-rc.d: 446: /etc/init.d/resin: not found
invoke-rc.d: initscript resin, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 resin-pro
E: Sub-process /usr/bin/dpkg returned an error code (1)



I'm have no idea on what to do.

Please advice,

Stevenson Lee

---

### Post by Rubi1200 on 2011-10-11
Try this command:

```
sudo dpkg --configure -a
```

and then

```
sudo apt-get update 

```
Let us know if this helps.

---

