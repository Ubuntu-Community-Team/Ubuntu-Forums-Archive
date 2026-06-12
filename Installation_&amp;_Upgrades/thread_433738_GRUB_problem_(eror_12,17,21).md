---
title: "GRUB problem (eror 12,17,21)"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by saurabh256 on 2007-05-05
I installed ubuntu 7.04 on external USB hard disk and getting grub errors

1. Error 21 when my external drive is not connected
2. Error 17 when I try to select winXP
3. Error 12 when I try tp select ubuntu 


when I boot from From Live CD and type the command the following is the output

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/hda2            1021        9728    69947010    f  W95 Ext'd (LBA)
/dev/hda5            1021        3570    20482843+   7  HPFS/NTFS
/dev/hda6            3571        9728    49464103+   7  HPFS/NTFS

Disk /dev/sda: 40.0 GB, 40060404224 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        4870    39110242+   f  W95 Ext'd (LBA)
/dev/sda5               2        4289    34443328+   7  HPFS/NTFS
/dev/sda6            4290        4798     4088511   83  Linux
/dev/sda7            4799        4870      578308+  82  Linux swap / Solaris

grub> find /boot/grub/stage1
 (hd1,5)

[B]Note: When I reboot from external hard drive find command shows me (hd0,5)
      I am not sure how to handle this scenario
[/B]
grub> geometry (hd0)
drive 0x80: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/hda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 4870/255/63, The number of sectors = 78242977, /dev/sda
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type unknown, partition type 0x82


ubuntu@ubuntu:/media/disk-1$ cat boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/sda

---

### Post by saurabh256 on 2007-05-05
I got the problem solved just now after going through lots of post.
I edited my menu.lst using gedit 
made the following changes.

root = (hd0,5)
boot=(hd0,5)
and changed the device map from
(hd0) /dev/hda  --> (hd1) /dev/hda 
(hd1) /dev/sda  --> (hd0) /dev/sda

Somewhere in the ubuntu forum I read that when we change the boot sequence in the BIOS and make USB drive prior then that is given the name hd0.
I still need to see whether my WinXP is running or not. Hope that this will help some one.

---

### Post by bulldog on 2007-05-05
The best way to this is to install GRUB to the external disk.
You only have to have the capability  to boot from a USB device.

If done like this,you can boot your internal windows drive like you did before,and if you want to use ubuntu,just select boot from USB device.
You want have to hassle with windows in your menu.lst.

---

