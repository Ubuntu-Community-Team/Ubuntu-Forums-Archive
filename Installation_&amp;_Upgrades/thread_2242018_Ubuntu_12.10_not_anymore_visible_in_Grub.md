---
title: "Ubuntu 12.10 not anymore visible in Grub"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by Pawel_Defee on 2014-08-30
I am running an older installation of Ubuntu 12.10. Upon a hard reset, it disappeared from Grub. I have tried multiple different instructions that I found with no success. The strange issue is that os-prober run from LiveCD correctly reports my partitions (sda4 for Win 8.1 and sda8 for Ubuntu 12.10). After mounting the Ubuntu partition and doing chroot, it only sees the sda4 (Win 8.1) partition, so update-grub does not put Ubuntu into the boot list.

Here is the boot info script on Ubuntu Pastebin:
[http://paste.ubuntu.com/8181215/](http://paste.ubuntu.com/8181215/)

Many thanks in advance for a suggestion on what else I could try..

---

### Post by claracc on 2014-08-30
ubuntu 12.10 has reached its end of life support a long time ago, so you cannot receive any security update neither to install new software will be easy. Trying to fix problem with an unsupported release is a little wate of time.

Perhaps the easiest way to solve the problem is to do a fresh install of a supported release as ubuntu 12.04 or 14.04

---

