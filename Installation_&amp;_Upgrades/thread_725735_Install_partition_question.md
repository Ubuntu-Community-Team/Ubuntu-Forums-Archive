---
title: "Install partition question"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by zxman on 2008-03-16
This is my first Linux install

System: HP Pavillion dv6707us laptop
Hard drive: 160GB SATA
Memory: 2GB
Installing: 7.10 from the Alternate CD (text installer)

I've already shrunk the NTFS partition and started the text installer.  I've selected "Guided - use largest continous free space"  and currently sit at the Partition disk screen.  It states:

<--- snip --->
The partition tables of the following devices are changed:
   SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
   partition #3 of SCSI1 (0,0,0) (sda) as ext3
   partition #5 of SCSI1 (0,0,0) (sda) as swap
<--- snip --->

1. Since the system has an SATA drive, is there a problem with it stating SCSI1?

2.  The system has 2GB of memory.  I've heard differing accounts of how large swap should be: same size as RAM, twice RAM, no more than 1GB.  How large should the swap partition be? 

Thanks from a noobie.

---

### Post by NightwishFan on 2008-03-16
I just use the 2x ratio. I have 1gb of ram so I use about 1.98gb swap. Yes I made it a fancy number that is slightly less than 2.0gb :)

---

### Post by Sef on 2008-03-16
> The system has 2GB of memory. I've heard differing accounts of how large swap should be: same size as RAM, twice RAM, no more than 1GB. How large should the swap partition be?


If you are doing some intensive gaming, video editing, or other memory intensive application, then it is best to have a swap of 1.5 -2 times.  I don't do anything really graphics intensive and barely use my 1 GB swap.  I don't really need it.

---

### Post by housam on 2008-03-16
Do back-up your data before doing any thing ( just in case )

---

