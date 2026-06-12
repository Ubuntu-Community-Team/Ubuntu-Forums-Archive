---
title: "Upgrading old laptop from 8.10 to 10.10 using USB-Stick"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by swissz on 2010-12-29
Hi!
I have an old laptop, in which the CD/DVD doesn't work and has no floppy.
I would like to upgrade the with Ubuntu 8.10 installation on the laptop without using a CD. I followed the instructions on the Ubuntu site to make a bootable USB-Stick. Unfortunatelly, the old machine can't boot from a USB-Stick. I was browsing the BIOS, and no relevant option was found. I tried to boot from the USB using the grub menu according to [1] with no success, the GRUB can't see my USB drive (find (hd1,0) ).
I would like to find a somewhat simple way to boot either from the USB-Stick, or from the ISO file or extracted ISO file on the HDD by either editing the GRUB or making some changes in my existing 8.10 installation.

[1] [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

The solution can be found in [1] under "Booting the kernel from an internal hard drive", it works!

---

