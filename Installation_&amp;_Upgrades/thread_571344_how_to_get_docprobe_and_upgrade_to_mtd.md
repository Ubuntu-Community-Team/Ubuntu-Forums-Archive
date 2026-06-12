---
title: "how to get docprobe and upgrade to mtd"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by kandhala on 2007-10-09
Hi all i am using Linux-generic kernel on ubuntu 7.04 which is "linux-headers-2.6.20-16".
 i want to upgrade this kernel to generate and mount the file system for embedded target system

1) for the mtd support and my kernel was presently not configured to support mtd 

2)kernel not recognising any block device /mtd [ not a block device ] error when i try to mount or create 
ramdisk image

3) to modify docprobe.c in drivers/ mtd /devices to undef "DOC_SINGLE_DRIVER" 
with /dev/mtd's kernel saying it is not block device when i want to mount.

Unfortunately my kernel/drivers/mtd/devices dont have any files except Kconfig and Makefile

i request some one to guide and help me how to upgrade and get the docprobe.c and other files.

thanks
kandhala

---

