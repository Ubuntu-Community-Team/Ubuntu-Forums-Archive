---
title: "Unable to uninstall or install galileo"
date: 2015-01-08
forum: Installation &amp; Upgrades
---

### Post by susja on 2015-01-08
Hello,
I tried to insall galileo in order to sync my Fitbit with Ubuntu 12.04.
Installation was errors and I tried to uninsall it. Now I'm stuck and can't neither uninsall or install. I've got this error when try to un-install:
**
sudo apt-get remove galileo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  galileo
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 205 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 321770 files and directories currently installed.)
Removing galileo ...
invoke-rc.d: unknown initscript, /etc/init.d/galileo not found.
dpkg: error processing galileo (--remove):
 subprocess installed pre-removal script returned error exit status 100
No apport report written because MaxReports is reached already
                                                              invoke-rc.d: unknown initscript, /etc/init.d/galileo not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 galileo
E: Sub-process /usr/bin/dpkg returned an error code (1)

**
Could someone please help me uninstall or install properly galileo?
Thanks in advance

---

### Post by susja on 2015-01-09
Well ... I noticed in the error log this line:
/etc/init.d/galileo not found.
I created this file and after that I was able to uninsall and then correctly install it.
Sorry for confusion ..

---

