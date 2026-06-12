---
title: "Forward Button is Grey when Installing"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by RadShad on 2011-03-04
When I try to install Ubuntu 10.10, it gives me a grey forward button after clicking and does not advance. I tried and waited a while, no deal. I tried doing install of 64 bit and 32 bit but still no deal, it always gets stuck at this part. Also doing a USB install. 

[IMG]http://img20.imageshack.us/img20/4655/screenshot1mw.png[/IMG]

It doesn't show it but the mouse is in thinking mode and spinning.

any help?

---

### Post by Hedgehog1 on 2011-03-05
RadShad,

I have seen this when the current partition layout on your disk does not allow more partitions to be added.

To check this (and walk you through fixing it), would you please:

Boot off the live CD, Select 'try', then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by RadShad on 2011-03-05
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00008c6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       58336   468581376   83  Linux
/dev/sda2           58336       60802    19802113    5  Extended
/dev/sda5           58336       60802    19802112   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders
Units = cylinders of 1892 * 512 = 968704 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           5        4138     3909696    b  W95 FAT32
```

Here you are :D

---

### Post by RadShad on 2011-03-05
It's all good now. I got past that part and I don't know how but it is installed :D

---

### Post by Hedgehog1 on 2011-03-06
I am happy it installed.

I, too, don't quite know how it happened, but I suppose it doesn't matter.

You are running Ubuntu - and that is what we both wanted.

***The Hedge***

:KS

---

