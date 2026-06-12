---
title: "How to boot Ubuntu after installing?"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by kuntau on 2010-06-14
Hello,

After finish installing ubuntu from CD it ask me to restart then after restart I only find Windows OS to boot, not ubuntu.

I got 3 hdd
1) 160G 2 partitions runing XP
2) 500G 8 partitions (this hdd i'm installing ubuntu
3) 500G 4 partitions runnning Win7 64

I tried using EasyBCD as suggested [here]("https://help.ubuntu.com/community/WindowsDualBoot#Issues with Windows XP and NTFS") and I got this

[IMG]http://lh6.ggpht.com/_-q6kqVLAqhQ/TBZOFknZ66I/AAAAAAAAAR4/XxTZTv7Kaeo/s720/IMG_20100615_230156.jpg[/IMG]

After selecting the linux I got this

[IMG]http://lh5.ggpht.com/_-q6kqVLAqhQ/TBZOL8F3ehI/AAAAAAAAAR8/OmxjVQeJe60/s720/IMG_20100615_230308.jpg[/IMG]

and after I select that it give me this error

[IMG]http://lh6.ggpht.com/_-q6kqVLAqhQ/TBZOUmd1zLI/AAAAAAAAASA/7NgFH2QT2q8/s720/IMG_20100615_230325.jpg[/IMG]

this what inside gutsy gibbon

[IMG]http://lh6.ggpht.com/_-q6kqVLAqhQ/TBZOZxFE9fI/AAAAAAAAASE/1ZxHKJ2tvCQ/s720/IMG_20100615_230341.jpg[/IMG]

What inside my bootloader

> There are a total of 3 entries listed in the Vista Bootloader.
Bootloader Timeout: 30 seconds.
Default OS: Windows 7 Ultimate (recovered) 

Entry #1

Name:  Earlier Version of Windows
BCD ID:  {ntldr}
Drive:  C:\
Bootloader Path:  \ntldr

Entry #2

Name:  Windows 7 Ultimate (recovered) 
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #3

Name:  Ubuntu Linux
BCD ID:  {636c4007-76ba-11df-b3be-964638a71002}
Drive:  I:\
Bootloader Path:  \NST\nst_grub.mbr

---

### Post by darkod on 2010-06-14
I think you were mislead. The EasyBCD option is for users who don't want to remove windows bootloader from the MBR of their disk, or can't remove it.
Besides, in your case with three disks, you can still keep windows bootloader on two of them. Just install grub2 to the MBR of the ubuntu disk, don't use EasyBCD.

Boot with the ubuntu cd in live mode (Try Ubuntu), and in terminal run:

sudo fdisk -l

You can just install grub2 to the MBR now. Post the results of fdisk so we can see the disks and partitions.

---

### Post by kuntau on 2010-06-14
Hi thx for the reply.. here is result of fdisk -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2f62f19e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51199999+   7  HPFS/NTFS
/dev/sda2            6375       12749    51199999+   7  HPFS/NTFS
/dev/sda3           12749       19123    51199999+   7  HPFS/NTFS
/dev/sda4           19123       60802   334784537    f  W95 Ext'd (LBA)
/dev/sda5           19123       25497    51199999+   7  HPFS/NTFS
/dev/sda6           25497       38246   102399999+   7  HPFS/NTFS
/dev/sda7           38246       46100    63088018    7  HPFS/NTFS
/dev/sda8           50994       60802    78781464    7  HPFS/NTFS
/dev/sda9           46100       50787    37648384   83  Linux
/dev/sda10          50787       50993     1658880   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2f62f19c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9258    74364853+   7  HPFS/NTFS
/dev/sdb2            9259       19457    81923467+   f  W95 Ext'd (LBA)
/dev/sdb5            9259       19457    81923436    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2f62f192

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15052   120905158+   7  HPFS/NTFS
/dev/sdc2           25497       50992   204796620    7  HPFS/NTFS
/dev/sdc3           50993       60801    78790792+   7  HPFS/NTFS
/dev/sdc4   *       15053       25496    83891430    7  HPFS/NTFS

Partition table entries are not in disk order

```

---

### Post by kuntau on 2010-06-14
> **darkod said:**
> I think you were mislead. The EasyBCD option is for users who don't want to remove windows bootloader from the MBR of their disk, or can't remove it.
Besides, in your case with three disks, you can still keep windows bootloader on two of them. Just install grub2 to the MBR of the ubuntu disk, don't use EasyBCD.

Boot with the ubuntu cd in live mode (Try Ubuntu), and in terminal run:

sudo fdisk -l

You can just install grub2 to the MBR now. Post the results of fdisk so we can see the disks and partitions.

How do I install the grub2 to the MBR? Thx

---

### Post by darkod on 2010-06-14
From live mode do:

sudo mount /dev/sda9 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and make the ubuntu disk first in hdd boot order in BIOS, if it isn't. You should see grub2 at boot with windows entry which should allow you to select between XP and 7 in a second menu.

---

### Post by kuntau on 2010-06-14
ok thx darlod. gonna try now will report back soon. thx

---

### Post by darkod on 2010-06-14
Don't forget that in the windows boot files you still might have the wrong ubuntu entry. Just use EasyBCD again to remove it, I think you should be able to remove it with that.

---

### Post by kuntau on 2010-06-14
Finally it worked!!

Damn the solution so simple and I just wasted 2 days of my precious life on finding solution on my own.

Thanks darkrod

---

