---
title: "How to install Ubuntu 10.10 dual boot with Windows 7"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by soltero5965 on 2010-12-22
Hello i've tried this once but it made my desktop inoperable maybe along the installation some things went wrong.
I have this MSi all in one touchscreen desktop model AIO 2010 with windows 7 home premium installed on it and i want to dual boot with ubuntu 7 
Is there any step by step guide on how to do it properly?
    
MSi All in one model AIO 2010

AMD Athlon(tm) X2 Dual core Processor 3250e
Hard disk is sata 320 g
ATI Radeon HD 3200 Graphics

any help on how to properly install Maverick Meerkat
Thank you!

---

### Post by Mark Phelps on 2010-12-22
Unless you know for sure that your PC has less than 4 primary partitions on your hard drive, the first thing to do is to boot into the Ubuntu Live CD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on your drive.  Post the results back here.

Then, presuming you have less than 4 primary partitions, the next two things you need to do BEFORE you try to install Ubuntu ...

1) Go into the Win7 Backup feature, create and burn a Win7 Repair CD.  You might need this later to restore the Win7 boot loader files if problems happen during the dual-boot installation.

2) Go into the Win7 Disk Management utility and use it to shrink the Win7 OS partition.  Don't use the Ubunutu installer to do this as that sometimes results in corruptions to the Win7 OS partition.

---

### Post by Elfy on 2010-12-22
Closed - do not post duplicates - thank you

---

