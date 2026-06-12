---
title: "Upgrade to lucid problem"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by ps2chiper on 2010-05-19
I just upgraded to lucid and I am now having this problem. I already tried a few things to fix it, but thing worked. Did anyone else encounter this problem.

Extracting templates from packages: 100%
(Reading database ... 269184 files and directories currently installed.)
Removing linux-backports-modules-2.6.31-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Cannot find /lib/modules/2.6.31-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-17-generic
dpkg: error processing linux-backports-modules-2.6.31-17-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-backports-modules-2.6.31-19-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-19-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Cannot find /lib/modules/2.6.31-19-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-19-generic
dpkg: error processing linux-backports-modules-2.6.31-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.31-17-generic
 linux-backports-modules-2.6.31-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by ps2chiper on 2010-05-19
I fixed it by doing this

root@host:~# mkdir /lib/modules/2.6.31-17-generic
root@host:~# mkdir /lib/modules/2.6.31-19-generic
root@host:~# apt-get autoremove

---

