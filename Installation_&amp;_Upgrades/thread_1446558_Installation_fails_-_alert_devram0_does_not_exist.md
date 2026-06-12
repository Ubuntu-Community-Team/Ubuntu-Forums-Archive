---
title: "Installation fails - alert /dev/ram0 does not exist"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Doogle999 on 2010-04-04
Hi guys/gals,

I am trying to get Xubuntu on an old laptop (1999) that currently has XP on it.

It has a broken internal CD drive. However I have an external USB CD drive but the BIOS does not support booting from USB. So I installed GRUB and copied the Xubuntu CD contents onto the existing windows C: partition to get an install running as per these instructions ("The CD approach" - [https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows"))

The installation fails before the kernel can be loaded (I think) with this message:

```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/ram0 does not exist. Dropping to a shell!
```

My GRUB entry to boot the installation looks like this:

```
kernel (hd0,0)/ubuntu/casper/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd (hd0,0)/ubuntu/casper/initrd.gz
```

I followed the suggestion and "ls /dev/ram*" brings back a list of ram drives with ram0 present. I have googled a lot around this and read about the kernel args but can find no answers to this specific problem.

I am a newbie to this, any help much appreciated.

---

