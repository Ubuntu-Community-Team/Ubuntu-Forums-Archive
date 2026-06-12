---
title: "tried to resolve Ubuntu 12 Fn + F2 problem with Wifi on Inspiron 1501"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by LinuxPeon on 2013-06-05
please assist:

I have tried to resolve the issue with my Dell Inspiron 1501's Wifi when I installed Ubunut 12 on it (see below).
I was able to switch on my Wifi with Fn + F2 under Ubunut 9.
Also, I installed Ubunut 12 on an 8Gb USB (not sure if it matters though).

thank you :)
========================
lspci -vvnn | grep 14e4

result:  BCM4312

===============
joshua@Linux:~$ sudo dpkg -i *b43*.deb
(Reading database ... 141828 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:012-1build1 (using b43-fwcutter_i386.deb) ...
Unpacking replacement b43-fwcutter ...
Setting up b43-fwcutter (1:012-1build1) ...
--2013-06-04 18:49:43--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org (downloads.openwrt.org)... failed: Name or service not known.
wget: unable to resolve host address 'downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--install):
 subprocess installed post-installation script returned error exit status 4
Processing triggers for man-db ...
Errors were encountered while processing:
 b43-fwcutter

===========================
joshua@Linux:~$ sudo dpkg -i dkms*.deb
Selecting previously unselected package dkms.
(Reading database ... 141828 files and directories currently installed.)
Unpacking dkms (from dkms_2.2.0.3-1ubuntu3.1_all.deb) ...
Setting up dkms (2.2.0.3-1ubuntu3.1) ...
Processing triggers for man-db ...
====================
joshua@Linux:~$ sudo dpkg -i bcmw*.deb
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 141875 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_i386.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-23-generic
Building for architecture i686
Building initial module for 3.5.0-23-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-23-generic/updates/dkms/

depmod.............

DKMS: install completed.
FATAL: Module ssb is in use.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic

---

### Post by LinuxPeon on 2013-06-05
I do not have access to Ethereal, so I tried to make it work by downloading all files from another PC.

---

