---
title: "Replacing Fedora 13 w/ Ubuntu 10.04 on dualboot w/ win7"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by fubeca6 on 2010-10-05
So, to be candid, i am a complete linux/ubuntu and general computer N00b - as will quickly become apperent - so please bare with.

To make a long story short: I installed Fedora13 to dualboot w/ my windows 7. I quickly found out that I don't care for fedora. I was referred to Ubuntu, and put Ubuntu 10.04 on in VirtualBox. Lo and behold, I like Ubuntu a WHOLE lot more! 

So, I promptly went to Disk Manager (in win7) and deleted the Fedora partitions (told you i'm a noob). Of course that was a poor choice, and I was only able to get my computer to boot again by reinstalling f13. neat.


So I did some research in the forums but wasn't actually able to find a solution to my particular situation. However, I did get enough info so that I can provide this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97804ced

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       34666   276912298    7  HPFS/NTFS
/dev/sda3           34666       34730      512000   83  Linux
/dev/sda4           34730       60802   209424384    5  Extended
/dev/sda5           34730       60802   209423360   8e  Linux LVM

Disk /dev/sdb: 2020 MB, 2020904448 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         245     1967931    6  FAT16


SO what i was thinking is go back to Disk Manager, delete partitions sda 3,4, & 5 (the linux ones), then reboot from the Ubuntu live disk? But I don't know what the sdb1 partition is??

Please help! Thanks

---

### Post by mikewhatever on 2010-10-05
Deleting the Fedora partitions and using the space to install Ubuntu sounds about right. /dev/sdb is another storage device, an sd card or usb stick. Don't you have anything like that attached?

---

### Post by coffeecat on 2010-10-05
> **fubeca6 said:**
> SO what i was thinking is go back to Disk Manager, delete partitions sda 3,4, & 5 (the linux ones), then reboot from the Ubuntu live disk?

You don't even have to use Windows' Disk Manager. Start booting up with the Ubuntu live CD and when you see the two small nondescript icons at the bottom of the screen tap the space bar and you'll get the language chooser followed by the traditional CD menu. Choose the first entry and you'll be booted (slowly) into the Ubuntu desktop. Before you start the installer, go to System > Administration > Gparted Partition Editor. You can delete the Linux partitions from there. Close Gparted and start the installer. When you get to the partitioning stage choose 'use largest free continuous space' (or words to that effect) and the rest should be plain sailing.

Instead of using Gparted to delete the partitions, you could choose the manual (advanced) option in the partitioning part of the installer but it looks as though Fedora has set you up with a tiny separate boot partition (which is a pointless nuisance imo) so you would be better off deleting the lot as above.

By the way, when you deleted the Linux partitions first time, you took out stage 2 and the configuration files for grub - the bootloader - which are in the Linux root partition. Something to bear in mind for the future. Actually they were in the boot partition which did give it some point, but I find a separate boot partition to be an unnecessary complication. It's a Fedora obsession.

> **fubeca6 said:**
>  But I don't know what the sdb1 partition is??

Agreed with what mikewhatever said. It's a 2GB device formatted FAT16. Must be a USB pendrive or SD card.

---

### Post by fubeca6 on 2010-10-05
Thank you both so much. Coffeecat, i did exactly as you said and got it all worked out. Thank you again for your help, it's very much appreciated!

---

