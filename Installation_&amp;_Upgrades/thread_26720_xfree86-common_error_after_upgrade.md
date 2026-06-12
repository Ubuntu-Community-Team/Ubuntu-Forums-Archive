---
title: "xfree86-common error after upgrade"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by slapphappy on 2005-04-13
david@sabre ~ $ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up xfree86-common (6.8.2-10) ...
update-rc.d: /etc/init.d/xfree86-common exists during rc.d purge (use -f to force)
dpkg: error processing xfree86-common (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 xfree86-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have fried upgrading xfree86 with the -f switch and it will not go.  I get errors when installing just about anything.  Any ideas?

---

### Post by Leif on 2005-04-18
Xfree is dropped in hoary. Use apt-get install xserver-xorg to change to it.

---

