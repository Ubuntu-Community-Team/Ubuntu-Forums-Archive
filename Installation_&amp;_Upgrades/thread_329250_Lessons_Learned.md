---
title: "Lessons Learned"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by wmcginnis on 2007-01-01
Nobody should have to suffer what I had to go through. I had another Linux distribution, I wanted to get rid of. I have 3 hard drives and 8 partitions. Still, installing Ubumtu should have been more intuitive.  In the end, I wanted a dual-boot Windows and Ubuntu system. Here are my observations - please fell free to correct as necessary.

Lesson Learned #1 - Uninstalling another Linux distribution
If another distribution is installed and you need to uninstall it, simply remove that Linux 
partition and the swap partition. Any partition manager will do this, but gpart that comes 
with most Linux distributions is free and will do the same thing. If you installed grub or 
another boot loader, you can uninstall it by booting with the Windows XP CD and selecting 
"Repair Console". After selecting your Windows installation and typing in the Administrator 
password, just type "fixboot", then "fixmbr", without the quotes. Remove the CD and reboot. It should boot directly into Windows.

Lessson #2 - Installing Ubuntu, the easy way.
Burn Ubuntu to a DVD (A CD does not have a large enough capacity or older readers can't use 690 MB CDs. During installation, select manually edit partition table and gpart will start. Create a new partition larger than 2 GB and install / (root) to it (make it active). Note the drive designation (something like hda 0/1) Create another partition (greater than 512 MB) and make it the swap drive. Do no try to install to an existing ext3 (Linux) drive and select format - it will fail. Ubuntu must be installed on unallocated drive space and create its own partitions using gpart.

Lesson #3 - Fixing the grub boot manager menu.
During the Ubuntu installation, install Grub Boot manager to the Master Boot Record (mbr). After Ubuntu installs, reboot your computer. If you select Ubuntu and get an error 22 - partition missing, you can fix it right in the boot menu. select Ubuntu in the grub menu and type "e", without the quotes, for edit. Type in the drive designated during the install (hda (0/1)). hit return and type "b" to boot. If you get another "Error 22" or "can't boot off this partition" error, you typed in the wrong value. Keep trying different values until Ubuntu boots - you can't hurt anything, you'll just keep on gett Error 22's until you find the right partition with Ubuntu installed.
After booting to Ubuntu, try booting to Windows. Both should work and voila - you have a 
dual-boot, Windows and Ubuntu system.

---

### Post by dasunst3r on 2007-01-01
Good!  Only one addition:
As far as "uninstalling" Linux is concerned, remember that the partitions for Linux remain and that you'll have use something to resize your Windows partition (e.g. PartitionMagic).

How good is Linux with resizing NTFS partitions these days?  I haven't done that in a while. :P

---

### Post by bulldog on 2007-01-01
Use the gparted live cd and boot from it,partition as you like and install ubuntu from the live cd in the already created partitions.
Works like a charm this way.

The gparted on the live cd should be similar as the gparted live cd, but it isn't.
This is come by so many times,a little search should have told you how to partition your drive.

---

