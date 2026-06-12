---
title: "Dual boot setup question"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by Sematary on 2010-03-15
If you are going to set up a box with both Windows and Linux, which should get installed first, or does it matter?

---

### Post by leorolla on 2010-03-15
Yes, it does matter.

Best thing in my opinion:

Partition with Ubuntu installation disk
Install Windows
Test Windows
Install Ubuntu

A typical partitioning scheme:

NTFS for Windows
FAT32 for your documents
EXT3 for Ubuntu
Swap

In this order.

Installing Ubuntu last will allow the linux Boot Manager GRUB to take control of the boot. It will normally recognize that you have Windows installed and will ask you whether to start windows or linux every time you turn on the PC.

---

### Post by oldfred on 2010-03-15
I agree with leorolla except I would also make the shared data partition NTFS also. FAT cannot store files over 4GB and is not journalized, so it does not recover from errors well.

It is not that difficult to reinstall boot loaders but it adds extra unnecessary steps that can be saved by doing it in the correct order. If you have lots of hard drive space you can also add additional partitions for /home or for /data, but are not necessary if just starting out. The /home makes it easy to do a clean update and save you settings as all user settings are in /home. 

I had root, swap and a shared partition with winXP for three years before adding additional home and data partitions as I had a better idea of how large to make them. I also just converted my shared FAT to NTFS with my upgrade to Karmic.

---

### Post by presence1960 on 2010-03-15
If you are starting from scratch it is a little bit easier to install windows first, but it is not necessary. If you put windows on after linux then you will have to restore GRUB to MBR as windows will overwrite it. For even a newbie that is a a 30-60 second process using the ubuntu Live CD.

+1 oldfred on the NTFS partition for shared data.

---

### Post by tom4jean on 2010-03-16
I used this guide with very good results.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I had windows 7 on first, so no choice on what to start with.
I partitioned windows 7 from within windows 7 as the guide says to.
I then installed Ubuntu to the free space and put the boot loader on the Ubuntu partition and used easyBSD, as suggested in the guide under the MBR section, so I could use and keep the windows boot loader.
If you use easyBSD you need the beta 2.0 release to interact with grub2. the regular release works with grub 1.

---

