---
title: "webmin / libmd5-perl"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by kfsone on 2010-05-05
Trying to install webmin on Ubuntu 10.4 server; it depends on libmd5-perl which does not appear in the Ubuntu repositories.

I tried the instructions used previously for Karmic ([http://ubuntuforums.org/showthread.php?t=1295178](http://ubuntuforums.org/showthread.php?t=1295178)) but the apt-get install -f just wants to remove webmin.

Procedure:

[INDENT]wget wget [http://www.webmin.com/download/deb/webmin-current.deb](http://www.webmin.com/download/deb/webmin-current.deb)
sudo dpkg -i webmin_*.deb
sudo apt-get install -f
[/INDENT]

Output

> root@tracsvn:~# dpkg -i webmin_1.510_all.deb
Selecting previously deselected package webmin.
(Reading database ... 26367 files and directories currently installed.)
Unpacking webmin (from webmin_1.510_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 webmin
root@tracsvn:~# apt-get install libmd5-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libmd5-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmd5-perl has no installation candidate
root@tracsvn:~# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  webmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.


---

### Post by kfsone on 2010-05-05
Never mind, stupid local web cache.

[http://ubuntuforums.org/showthread.php?t=1467513&highlight=libmd5-perl](http://ubuntuforums.org/showthread.php?t=1467513&highlight=libmd5-perl)

---

