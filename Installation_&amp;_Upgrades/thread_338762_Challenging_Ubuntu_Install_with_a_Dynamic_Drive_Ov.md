---
title: "Challenging Ubuntu Install with a Dynamic Drive Overlay (DDO), and GRUB on floppy"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by kbehel on 2007-01-14
I've got a challenging install situation that I can't seem to resolve. I know it is possible to make it work in the desired setup, because I did it last week with Debian (Sarge), however I'd like to try Ubuntu instead.

I have an old system with Windows 98 that has the 8GB hard drive limitation. I have two hard drives, both Maxtor, one is 60Gb the other is 80gB. I can make the larger drives work with Windows 98 by using Maxtors Maxblast software to install a DDO (dynamic drive overlay) to the boot drive's master boot record. 

I want to install Ubuntu with the drives configured as the following:

(disk1) /dev/hda1:  60Gb, with the DDO in the MBR, 1 Win 98 partition
(disk2) /dev/hdb: 80GB all as a Linux disk (Ubuntu's partitioner makes a few partitions here).

Using Ubuntu's normal installer wipes out the DDO in the MBR, so I cannot use my Win98 OS anymore (remember the DDO MUST be loaded for the Win98 OS to work). 

Using the alternate install CD I was never given the option to place GRUB anywhere (disk 1 or disk 2.... odd because I thought it was supposed to ask). However I think the only option I am supposed to get is to the hard disk.

What I need to do is install GRUB to a floppy as a part of this install. This is what is supposed to work best with the DDO setup like I have. This is also what was working fine for me with my Debian install until I trashed it. I'm not sure how to install GRUB to the floppy. Perhaps I just need to learn how to use the Rescue mode and configure GRUBmanually, though I don't know enough about GRUB to do this.

Is is possible to install GRUB to a floppy instead?
Is is possible to setup GRUB manually for a floppy? I've got the Ubuntu install on the disk, but I need GRUB on a floppy for it to work.

thanks,

Kevin

---

