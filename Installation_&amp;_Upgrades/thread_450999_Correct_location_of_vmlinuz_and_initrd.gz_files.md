---
title: "Correct location of vmlinuz and initrd.gz files"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by tblast on 2007-05-21
I've been trying to do a hard drive install from a Xubuntu6.06LTS iso by having the iso on a HD fat32 partition and loading the kernel using 'linld'. 

I downloaded hd-media files vmlinuz and initrd.gz as in the following addresses :

[http://mirror.pacific.net.au/linux/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://mirror.pacific.net.au/linux/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)

and I boot using linld. 

Everything is fine and the install works until it searches for the kernel modules at which point it states there is a clash of kernel versions between the installer downloaded from the above address and the one from the iso. No modules get loaded as a result.

I know this method of install works because I've used it a few times for installing Debian.

Can someone suggest where I could download the correct hd-media files for Xubuntu6.06LTS? Or is this a generic install problem with Ubuntu and general difference between Debian and Ubuntu?

---

