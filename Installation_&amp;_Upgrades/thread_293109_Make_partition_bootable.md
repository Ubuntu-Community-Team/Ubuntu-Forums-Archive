---
title: "Make partition bootable"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by JoeS on 2006-11-04
I installed breezy badger and divided my hard drive into three partitions: root, swap and home. It asked me if I wanted to make these partitions bootable.  I did for the root partition. Can someone explain what this means?

---

### Post by amohanty on 2006-11-05
The short version:
When the computer boots up, it will go through all the HDDs in the system starting with the primary master and all other devices listed in the BIOS boot order, looking for MBRs ([http://en.wikipedia.org/wiki/MBR](http://en.wikipedia.org/wiki/MBR)) on HDDs or boot images on CDs and floppies.

The MBR usually contains a bootloader which has pointers to partitions where the core operating system image is which willbe used to start up the system. When you set / as bootable, the GRUB bootloader will look for a folder called boot on that partition (I have different partitions for .boot and / for e.g. - so only my /boot partition is bootable) and then load the kernel image from there.

The long answer:
look at tldp.org or google.

HTH
AM

---

