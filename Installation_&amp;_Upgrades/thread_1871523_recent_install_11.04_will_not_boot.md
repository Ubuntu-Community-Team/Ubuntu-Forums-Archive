---
title: "recent install 11.04 will not boot"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by I_need_your_help on 2011-10-29
Hi, I just tried installing ubuntu from a bootable usb stick on my windows 7 desktop. I wanted to create a dual boot system. After repartitioning my drive and installing all the necessary files ubuntu will not boot from the grub startup menu. I tried reinstalling ubuntu from the usb drive but the same result happened. I am however able to boot up with ubuntu with the USB stick. I ran sudo fdisk -l and got the following results:

[PHP]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7830332a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1698    13631488   27  Unknown
/dev/sda2   *        1698       68013   532678839    7  HPFS/NTFS
/dev/sda3           68013       77826    78819329    5  Extended
/dev/sda5           76786       77826     8351744   82  Linux swap / Solaris
/dev/sda6           68013       75746    62114816   83  Linux
/dev/sda7           75746       76786     8347648   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4041 MB, 4041211904 bytes
128 heads, 63 sectors/track, 978 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         979     3946464+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(977, 127, 63) logical=(978, 101, 37)
[/PHP]


I also took a picture of what it says when I boot up in recovery mode.I guess I don't know what to do at this point. I don't have a lot of troubleshooting experience. Any assistance would be greatly appreciated. 

Thanks!

---

### Post by I_need_your_help on 2011-10-29
Does anybody have any suggestions? I really don't know how to solve the problem.

---

### Post by wojox on 2011-10-29
Fresh download ( preferably from the torrents ) and reburn at a low rate and try to install again.

---

