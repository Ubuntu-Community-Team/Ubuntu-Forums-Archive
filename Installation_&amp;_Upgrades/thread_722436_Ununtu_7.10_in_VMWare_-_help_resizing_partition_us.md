---
title: "Ununtu 7.10 in VMWare - help resizing partition using GParted Live CD"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by BrutusB on 2008-03-12
So I downloaded the Ubuntu  VMWare image with v7.10.  It comes stock with a 7GB virtual disk so I resized the disk to 32MB using the VMWare disk manager - no problem.  Then I booted with the GParted Live CD in an attempt to resize the partition.  This is what I see:

[IMG]http://i27.tinypic.com/jz6ves.jpg[/IMG]

Why is that partition marked as unknown?  I can't resize it.

---

### Post by BrutusB on 2008-03-12
I've also tried several different versions of GParted LiveCD to no avail.

---

### Post by BrutusB on 2008-03-12
What type of file system is Linux LVM ?

```

steve@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 34.3 GB, 34359738368 bytes
255 heads, 63 sectors/track, 4177 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bef39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        4177    33302745    5  Extended
/dev/sda5              32        1044     8136891   8e  Linux LVM
steve@ubuntu:~$ 


```

---

