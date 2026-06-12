---
title: "Help with booting non-Live from a USB flash drive"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by floepie on 2010-03-15
I have an 8GB Sandisk Cruzer, which reportedly works just fine booting Linux.  It does have U3 still present on one of the partitions, but this should not pose any problems either.  I also have a 2GB FAT32 partition for storing Windows stuff.  The rest (5.7GB) I have reserved for Ubuntu.  Windows reports this as an active partition, and the Ubuntu boot CD reports this partition as dev/sdb5.  I have installed Ubuntu from the Desktop CD to the USB partition using the guided install (largest continuous free space) and selected the boot (grub) location on the same partition (sdb5), as I'd rather not modify my existing windows bootloader.  A 300MB swap partition also exists on the drive. 

When I attempt to boot the USB drive from either my laptop (Inspiron 1505) or desktop (Abit IP35 Pro), only a blinking dash (or underscore) appears with no LED activity on the flash drive.  

Could it be that the MBR of the flash drive needs to be aware that the grub install is located at sdb5?  I'm really pretty new at this.  Thanks for any help.

---

### Post by Mighty_Joe on 2010-03-16
I've successfully used an 8GB Sandisk Cruzer, but only after removing U3.
I'd advise you do not use a swap partition on your flash drive.  Flash memory will wear out eventually and swap is particularly write-intensive.
I posted the procedures I used to create a full install on a USB drive [here]("http://ubuntuforums.org/showthread.php?t=1193680&highlight=partition+table").  The links have other suggestions for speeding up your install.

---

