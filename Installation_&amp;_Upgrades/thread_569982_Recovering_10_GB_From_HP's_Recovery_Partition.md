---
title: "Recovering 10 GB From HP's Recovery Partition"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by P4rD0nM3 on 2007-10-07
Hello, I have an old HP a500n lying around and I recently installed Ubuntu 7.04 in it. I have 80gb of hard drive space, however Ubuntu only shows 70gb.

I think this is due to the way HP partitions the hard drive wherein it always saves around 10gb or more depending on what preloaded OS you choose in their website.

I was wondering is there a way to completely recover all the 80gb of hard drive space and give it all to Ubuntu. I want to completely remove any trace of HP or whatever is left from the old operating system.

I want the 80gb to look as if I just bought a new 80gb hard drive. Thanks.

---

### Post by por100pre1 on 2007-10-07
Yes you can just delete that partition but I suggest you to use with HP burning tool to save it to DVD or CD (if you have Windows installed), or request OEM restore disks at the HP web page. Be sure to remove any entries for that partition in GRUB if any. :)

EDIT: Read how to delete the partition [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00810279&lc=en&cc=us&dlc=&product=3304190&rule=9275").

---

### Post by P4rD0nM3 on 2007-10-07
Well I already saved it in a CD. Now I'm just running Ubuntu on a LiveCD.

When I did sudo fdisk -l, it showed me this line.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9565    76830831   83  Linux
/dev/hda2            9566        9729     1317330    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris


It showed 80GB. Did I format everything now? I'm not quite sure...because when I boot from the HDD. It just says 70GB.

---

### Post by logos34 on 2007-10-07
It may be advertised as an 80 GB hard drive and fdisk may show that, but you should actually have ~74.5 GB of disk space ([as seen by the OS]("http://www.hardwaresecrets.com/printpage/482/1")).  

So that HP partition may have been only around 4.5 GB....The OS is only showing the formattted space.  Maybe its just sitting there as unallocated space.  Post a screenshot of Gparted--that will show the entire disk.

---

