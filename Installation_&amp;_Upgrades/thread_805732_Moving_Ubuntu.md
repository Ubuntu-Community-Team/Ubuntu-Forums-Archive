---
title: "Moving Ubuntu"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by dhoni on 2008-05-24
Hi guys,
I have got 2 partitions, C drive and D drive, I have just installed Ubuntu on C drive and have just found out I have got 48 MB left, on D drive I have got around 40 gig, is it possible to move Ubuntu to the D drive partition, or create a new partition for Ubuntu to go on?
thanks

---

### Post by unutbu on 2008-05-24
Please post the output to
```
sudo fdisk -l
```

---

### Post by dhoni on 2008-05-24
Hi,
It wont let me do it, i type in the password and it still does not work, it still has the $ sign at the end, i closed it and tried sudo su, it still didn't work.

---

### Post by dhoni on 2008-05-24
sorry, figured it out, here is the output to sudo fdisk -l
kishen@kishen:~$ sudo fdisk -l

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dd10dd1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1250    10040593+   7  HPFS/NTFS
/dev/hda2            2551       10011    59930482+   7  HPFS/NTFS
/dev/hda3            1622        2550     7462192+   5  Extended
/dev/hda4            1251        1621     2980057+  83  Linux
/dev/hda5            1647        2139     3959991   83  Linux
/dev/hda6            2140        2238      795186   82  Linux swap / Solaris
/dev/hda7            2239        2550     2506108+  83  Linux
/dev/hda8            1622        1646      200749+  82  Linux swap / Solaris

Partition table entries are not in disk order


I have also got pclinux installed on C drive.

---

### Post by unutbu on 2008-05-24
Hello dhoni, one of the problems here is the windows terminology of "C drive" means nothing specific in linux. In linux the partition are referred to as /dev/hda1, /dev/hda2, etc. fdisk gives a view of your hard drive as seen by linux. Can you tell me on the table below which partition contains the Ubuntu system you wish to move?

```
Device Boot Start End Blocks Id System
/dev/hda1  * 1 1250 10040593+ 7 HPFS/NTFS            10.3GB    C drive?
/dev/hda4 1251 1621 2980057+ 83 Linux                3.0GB
/dev/hda3 1622 2550 7462192+ 5 Extended
/dev/hda8 1622 1646 200749+ 82 Linux swap / Solaris  0.2MB
/dev/hda5 1647 2139 3959991 83 Linux                 4.0GB
/dev/hda6 2140 2238 795186 82 Linux swap / Solaris   0.8GB
/dev/hda7 2239 2550 2506108+ 83 Linux                2.5GB
/dev/hda2 2551 10011 59930482+ 7 HPFS/NTFS           61.3GB    D drive?
```

Are you currently running Wubi?
Are you using GRUB as your bootloader?

---

