---
title: "kernel update problems"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by goodtimes200 on 2012-08-13
I ran out of space on my boot partition so I followed the advice from:
[http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/](http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/)

However it has corrupted my file system and I get the following:
E: linux-image-3.2.0-26-generic: subprocess installed post-installation 
script returned error exit status 2
E: linux-image-3.2.0-27-generic: subprocess installed post-installation 
script returned error exit status 2
E: linux-image-3.2.0-29-generic: subprocess installed post-installation 
script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: initramfs-tools: subprocess installed post-installation script 
returned error exit status 1

I am at a loss as to how to resolve this issue. any help is appreciated

  df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        21G  6.2G   14G  31% /
udev             12G  4.0K   12G   1% /dev
tmpfs           4.8G  980K  4.8G   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none             12G   80K   12G   1% /run/shm
/dev/sda1       100M   85M  9.8M  90% /boot
/dev/sda3       5.4T  2.2T  3.0T  42% /home

---

### Post by helmut0 on 2012-08-13
I'm getting the same thing!!! I have installed 7 time already.

---

