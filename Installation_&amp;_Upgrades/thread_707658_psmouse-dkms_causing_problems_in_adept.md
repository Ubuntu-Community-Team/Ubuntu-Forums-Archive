---
title: "psmouse-dkms causing problems in adept"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by kybishop on 2008-02-25
I'm currently forced to update my computer from a terminal because of an error regarding psmouse-dkms.

Ever since psmouse-dkms was an available upgrade, it hasn't been able to install, and asks me to run dpkg --configure -a if I atempt to install anything through adept.

Here is there error message I get:
```
kyle@kyle:~$ sudo apt-get dist-upgrade
[sudo] password for kyle:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up psmouse-dkms (2.6.20-16.29-1) ...
Loading new psmouse-2.6.20-16.29-1 DKMS files...

Error! Cannot locate /usr/src/psmouse-2.6.20-16.29-1.dkms.tar.gz.
File does not exist.
dpkg: error processing psmouse-dkms (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psmouse-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help and/or explanation of what's going on (and what psmouse-dkms is) would be greatly appreciated.
 
Thanks, Kybishop

---

