---
title: "Ubuntu 12.04 will not boot"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by efgarro on 2012-07-13
I have just installed a new Solid State Drive into my Dell Laptop; installed Windows 7 Ult. - no problem - then proceeded to install Ubuntu 12.04 from a USB Stick - no problem - final message indicated that it was installed without issues and to proceed to restart. However, when I restarted, there is no option for Ubuntu and goes straight into Win 7. Bootloader no working? Any suggestions?

Cheers,

Eduardo

---

### Post by dino99 on 2012-07-13
a few questions:

 - is ubuntu installed on a bootable partition ? (need to be formated with the "boot" flag)

 - where is grub installed ?

 - is that pc with bios or uefi ?

---

### Post by darkod on 2012-07-13
In these cases I think sometimes it can install grub2 on the stick, because that was the first boot device to boot the install process.

Have you tried booting with the stick again to see if it will offer the Start Up menu, or the grub2 bootloader from the installation?

---

### Post by efflandt on 2012-07-13
It may be what Darknod says.  Judging from "Other" during install using install iso on USB, 12.04 no longer necessarily defaults to mbr of sda, and people have had problems with grub ending up on the USB they booted from instead of that.

It is not necessary to have the Ubuntu partition marked as boot, because grub does not pay attention to that.

I am not totally familiar with gpt partitions or uefi because I have no computer or drives that use that, but do know that something else is required if that is the case.

But first see if you get the grub menu when booting from the USB device, and if not, see what **sudo fdisk -l** shows for partition types or run [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by Version Dependency on 2012-07-13
It is not uncommon for Grub to install itself in the wrong partition, or on the USB stick.  Luckily, this is easily fixed: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can use a live CD or live USB of Ubuntu, then just follow the instructions on downloading the boot repair tool.  Install Grub to the proper partition and you should be good to go.

---

