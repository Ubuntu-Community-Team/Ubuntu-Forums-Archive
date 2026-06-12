---
title: "Installing server ubuntu from hard drive"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by croxis on 2006-12-17
I am attempting to install edgy server ubuntu from a hard drive onto itself on a legacy system.  The computer refuses to boot from the cd, so I put the hard drive on my personal system, partitioned a bootable ext3 and a swap space, and copied the install cd into /ubuntu/.  I am trying to use grub4dos (I am following [this]("https://help.ubuntu.com/community/Installation/FromWindows") wiki guide as it seems the most applicable), however the grub4dos floppy is reporting that it can't mount the partition.  The menu.lst entry contains:
> title Install Ubuntu
kernel   (hd0,0)/ubuntu/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd   (hd0,0)/ubuntu/install/initrd.gz

Thank you for any help!

---

