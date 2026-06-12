---
title: "No 'size:' option"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by aje500 on 2008-07-25
Hi All,

I'm trying to install Ubuntu from the Live CD, and want to keep my Windows XP installation intact. 

Reading the documentation, dual boot seemed like the way forward. I'm following the instructions [here]("http://doc.ubuntu.com/ubuntu/switching/dualboot-procedure.html").

I get to step 5, press enter, but there is no option to press 'size', as step 6 suggests. Instead, the screen just gives the option to change the file system (e.g. NTFS, FAT32, FAT16 etc) and a checkbox to format the partition.

Any help would be greatly appreciated.

Many thanks,

Allen

---

### Post by Kevbert on 2008-07-25
How is your hard disk(s) set up ?  If you have only one partition on the PC hard disk then you'll need to shrink it in order to install Ubuntu on a new partition.  
First go into windows and backup everything that's important (in case of mishaps).  Next defrag the disk.  Hopefully there will be a large empty space at the end of the disk.  Close windows and boot the Ubuntu CD.  You can now shrink the disk partition with the Partition Editor when you run the Ubuntu Live CD (it's an application under System).
If you have an empty partition (say 10Gb) this is ideal for installing Ubuntu.  Run the install program and when you get to partitioning select manual partitioning.  If you have the empty 10Gb partition delete it and then select the empty space and set the Swap partition to 2 x your memory (RAM) size.  The remaining free area is for your system and should be formatted as ext3 and / as the mount point.  Install the grub bootloader (I believe you have the option not to use it).  Windows will later appear as a menu item.
Hope this is of use.
I'm running XP Pro SP3, Ubuntu 7.10, 8.04, Kubuntu 8.10 on my main PC.

---

