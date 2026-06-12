---
title: "dpkg: error processing"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by jayashleysmith on 2008-03-20
jay@jay-laptopKDE:~$ sudo apt-get -f install
[sudo] password for jay:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cupswrapperdcp310cn (1.0.2-3) ...
touch: cannot touch `/usr/share/cups/model/brdcp310cn_cups.ppd': No such file or directory
/usr/share/cups/model/brdcp310cn_cups.ppd: No such file or directory.
dpkg: error processing cupswrapperdcp310cn (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperdcp310cn
E: Sub-process /usr/bin/dpkg returned an error code (1)
jay@jay-laptopKDE:~$


What can I do to try and solve this problem. It happenens every time I try to install any thing. GUI or Terminal!

Please Please help

JAS

---

### Post by dstew on 2008-03-20
How did you install cupswrapper? It does not seem to be an Ubuntu package. Did you get a Debian package from the manufacturer, or use alien with an .rpm?

EDIT: [Here]("http://www.mepislovers.org/forums/showthread.php?p=77128") is a thread describing how to get Synaptic to work again. You need to delete references to the bad package from the /var/lib/dpkg/status and /var/lib/dpkg/available files, and maybe references to the package in the /var/lib/dpkg/info directory too.

---

