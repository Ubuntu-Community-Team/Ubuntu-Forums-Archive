---
title: "Reading the Mind of Grub"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by rmcanany on 2007-06-02
I've got a new company-supplied really nice Dell M90 laptop running XP.

At home, I wanted to use the new machine, but run Ubuntu from an external USB drive.

Not wanting to trash my new machine, I took some advice and loaded Edgy onto the USB drive using an old machine where it was easy to disconnect the internal hard drive.

The old machine is gone and now I'd like to do a fresh intall with Feisty.  I'm worried that grub will sneak onto the internal drive.  If that were to happen, I don't have the original XP disks to fix it.  I gather that I can't use Super Grub Disk either because my machine has NTFS.

So I'm trying to find out what grub thinks is my USB disk.  From Edgy, if I sudo grub from the terminal, I can get the following information:

grub> geometry (hd0)
drive 0x80: C/H/S = 12161/255/63, The number of sectors = 195371568, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0xde
   Partition num: 1,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 14593/255/63, The number of sectors = 234441648, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type is fat, partition type 0xb

So right now it seems pretty obvious that (hd0) is my internal drive and (hd1) is my external USB disk.  At least, that's what I guess.

Running the installer on the Feisty Live CD, I get to the last dialog box and there's a little text box next to grub that says (hd0).  I can change that to (hd1).  Unfortunately, I can't make myself hit the OK button.  I'm just not sure I know what I'm doing.

Here's my question:  Is there a way I can be SURE that grub won't install to my internal drive?

Related question:  Assuming grub does get onto my internal drive, is there a way for me to fix it?  Don't forget, I don't have the XP CD and I'm running NTFS.

Sorry about asking the zillionth question on grub, but despite a lot of searching I never could find a post that addressed my exact situation.

TIA

---

### Post by mikewhatever on 2007-06-02
Yes there are ways to fix Windows boot loader.
[http://www.bootdisk.com/](http://www.bootdisk.com/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

hd1 looks the right choice.

---

### Post by rmcanany on 2007-06-03
Thanks for that.

Not to overthink this, but I ran across Herman's clever "Back up MBR" idea.
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

His trick is to boot a Live CD, then do the following:
sudo dd if=/dev/hda of=/home/ubuntu/OLDMBR.img bs=446 count=1

However, I wonder if I might need to adjust something for my setup.

Here's my partition table listing:

rmcanany@rmcanany-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       12161    97635037+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686   83  Linux
/dev/sdb2            5100        5354     2048287+  82  Linux swap / Solaris
/dev/sdb3            5355       14593    74212267+   b  W95 FAT32

Of course, I substituted "sda" for "hda" but my laptop has the Dell Utility as the first partition.  Would I need to adjust the command further to account for this?

---

### Post by confused57 on 2007-06-03
/dev/sda   =    the mbr on your sda drive
/dev/sda1 =    the first partition with the Dell Utility
/dev/sda2 =    the 2nd partition with Windows

Therefore, /dev/sda is your mbr that you want to backup...


Added:  It would still probably be a good idea to make a copy of the SGD...if your bios isn't capable of booting first from USB device, then you could use the Super Grub Disk to boot Ubuntu.

---

