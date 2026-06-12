---
title: "ALERT! /dev/mapper/ubuntu-root does not exist ! Dropin in to shell !"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by madone1 on 2012-01-20
I have problem booting my LVM after i have tryed this [How to for Reinstalling Ubuntu 9.04, 9.10, 10.04 over existing encrypted LUKS/LVM partitions.](http://ubuntuforums.org/showthread.php?t=1205372)
Every command described here is coming true without error including update of initramfs. Re using existing /home works. When i mount it manuly i see files on it. But i cant boot in LVM
I am geting this error

```
Loading initial ramdisk...
Volume group "ubuntu" not found
Skiping volume group "ubuntu"
and same error for all logical volumes ubuntu/root ubuntu/swap
then
ALERT! /dev/mapper/ubuntu-root does not exist ! Dropin in to shell !
```
and i end up in busybox initramfs

---

### Post by darkod on 2012-01-20
Does pvscan and vgscan show the expected devices and the VG?

---

### Post by madone1 on 2012-01-21
Pvscan and vgscan show the expected devices and the VG.
I can activate all 3 LV but when i try to boot with "exit" i get bunch of errors.
```
using makefile-style concurent boot in run level s
cant open /lib/init/vars.sh
cant open /lib/lsb/init-functions
cannot create /etc/mtab: read only file system
cant open /lib/init/bootclean.sh
....

```
and errors continue. When i do ctrl-c i log in as root but i get root@(none)#

From LiveCD i can open LV and see content of it.

---

