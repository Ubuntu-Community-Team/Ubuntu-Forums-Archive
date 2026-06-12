---
title: "Partition changing"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by siongz on 2007-11-28
Hi im new to linux... and ive realised that ive installed in the wrong partition... izzit possible to change partition or shrink one to increase my ubuntu's??

the result of "sudo fdisk -l" is as follow

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe233bc5d

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4534 36419323+ 7 HPFS/NTFS
/dev/sda2 4535 9729 41728837+ 5 Extended
/dev/sda5 9356 9417 498015 82 Linux swap / Solaris
/dev/sda6 4535 9354 38716587 83 Linux
/dev/sda7 9418 9729 2506108+ 83 Linux

and for df -h is as follow:

Filesystem Size Used Avail Use% Mounted on
/dev/sda7 2.4G 2.2G 42M 99% /
varrun 502M 104K 502M 1% /var/run
varlock 502M 0 502M 0% /var/lock
udev 502M 80K 502M 1% /dev
devshm 502M 0 502M 0% /dev/shm
lrm 502M 34M 468M 7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda6 37G 194M 35G 1% /boot
/dev/sda1 35G 2.5G 33G 8% /media/sda1
overflow 1.0M 48K 976K 5% /tmp


I believe ive installed ubuntu in sda7, will actually should be in sda6, any idea how to change partition or shrink the sda6??? thx in advance

---

### Post by Pumalite on 2007-11-28
Use Gparted Live CD.

---

