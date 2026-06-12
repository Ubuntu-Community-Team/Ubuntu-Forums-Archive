---
title: "Unable to install mondo rescue on fresh Ubuntu Trusty"
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by L0c8iT on 2015-07-20
I have recently installed Ubuntu 14.04 LTS on a 64 bit Core 2 Duo laptop.
System is updated (apt-get update and apt-get upgrade)
The system is uncluttered except I installed a proprietary driver for the Broadcom wifi (working fine).
I thought this would be a good time to back up the system before I foul it up accidentally.
So I tried to follow the directions in: [https://help.ubuntu.com/community/MondoMindi](https://help.ubuntu.com/community/MondoMindi) 
The contents of /etc/apt/sources.list.d/mondorescue-test.sources.list are now:
  deb [ftp://ftp.mondorescue.org/test/ubuntu](ftp://ftp.mondorescue.org/test/ubuntu) 14.04 contrib
  deb-src [ftp://ftp.mondorescue.org/test/ubuntu](ftp://ftp.mondorescue.org/test/ubuntu) 14.04 contrib
The subsequent results from apt-get update seem clean, and include several mondorescue items.
However, the next step results in errors I do not know how to resolve:

sudo apt-get install mondo afio buffer lzop mindi mindi-busybox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mindi-busybox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mindi-busybox' has no installation candidate

Any help extending my limited Linux knowledge would be much appreciated. Either getting this installed, or suggestions on alternate means of efficiently making full system backup and restores to/from a network mounted disk.
Thanks

---

### Post by helpee on 2015-07-20
Try to install just the dependancies first, then mindi-busybox. After that try sudo apt-get install mindi(tab tab) and tell us what you see. It should give a list of all available packages starting with 'mindi'

---

### Post by helpee on 2015-07-20
Also, if you still can't find the package, you can get it directly from

[https://packages.debian.org/squeeze/mindi-busybox](https://packages.debian.org/squeeze/mindi-busybox)

and then install the package with

sudo dpkg -i whateverThePackageNameIs.deb

This won't solve your problem later if you need to upgrade mindi-busybox, but you can always manually download the latest package and install it.

---

