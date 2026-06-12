---
title: "The easy way for USB Booting"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by rubenr999 on 2007-05-24
I was following the guide [https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)
and on the first step "Copying the files &#8212; the easy way", I found my USB device with fdisk -l
--
Disk /dev/sdb: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3816      976880    e  W95 FAT16 (LBA)
--
and downloaded [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/netboot/boot.img.gz)
Then as instructed by the guide I did zcat boot.img.gz > /dev/sdb1

When I see my USB directory, it is full of garbage, and I cannot delete it, I tried all forms of rm -rf
Please help! How can I clean my USB flash drive?

I am using Feisty Fawn since the latest alpha release

---

### Post by rubenr999 on 2007-05-24
And if somebody has a script to make a bootable USB it would be greatly appreciated, thanks

---

