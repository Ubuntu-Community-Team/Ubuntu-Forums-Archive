---
title: "Please help with install"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by cellularsnake on 2006-08-16
Hello, I'm trying to install Ubuntu from the Live CD.  My problem is that when I complete the install wizard and pick the areas of my HDD (NTFS Formatting) that I'd like Ubuntu to use the install seems to stop.  The disc dosent't spin and nothing appears on screen.  I'm a complete Linux noob and would greatly appericate any help in this matter.  Thanks in advance for any replies.

NOTE:I'm attempting to install Ubuntu on a new partition.

+CellularSnake

---

### Post by confused57 on 2006-08-17
First of all, is it a ship-it CD or from the Desktop iso downloaded & burned to cd.  Also, what are your system specs?...if you have less than 256 mb ram, it would be best to install with the alternate cd.
If all you have is the NTFS partition on your hard drive, you'll need to defrag your Windows a couple of times before resizing & partitioning from the installer.

See this thread for the Live CD:
[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

This is an excellent site for dualbooting with the alternate CD:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by goatflyer on 2006-08-17
Either way, you want to run the manual partitioner.

If you want to keep windows and dual boot:
Shrink the NTFS partition down to a size that still leaves a healthy amount of freespace for windows.  No need to defrag (this is true since Breezy). Ubuntu will create partitions from the freed-up space and install there.

If you want to wipe out your old windows completely, why keep NTFS? (that is a proprietary windows format).  Change it to ext3 and let the installer reformat it.

---

