---
title: "Complete GRUB Removal"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by philgenius on 2008-08-03
Hi. I just installed Ubuntu 7.10 on a USB connected 400 GB SATA hard disk. However, if I unplug the USB and boot, GRUB somehow pops up and returns an error (21 or 25). Is there a way I can remove this?

BTW, I do not have a Windows Recovery Disk, I have a Thinkpad T60. I need a complete removal of GRUB from my Windows hard disk. Using FIXBOOT C: and FIXMBR did not work. And I can't find a suitable fdisk v.1.2.1.

---

### Post by logos34 on 2008-08-04
Boot into ubuntu first and write grub to the mbr of the external drive

sudo grub-install /dev/sdb

Edit menu.lst:

gsksudo gedit /boot/grub/menu.lst

-change the 'groot' and 'root' lines to (hd**0**,?)

Download and burn a Super Grub Disk to restore windows boot loader.  Or make a [win98 boot floppy]("http://www.bootdisk.com/bootdisk.htm") (>fdisk /mbr).

---

