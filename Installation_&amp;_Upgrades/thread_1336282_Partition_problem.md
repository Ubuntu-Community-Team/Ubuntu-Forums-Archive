---
title: "Partition problem"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by cbustaam on 2009-11-24
Hi all, 
I've decided to install Ubuntu on my office PC. This PC has, by default, Windows XP and a hard disk of 150 Gb with two NTFS partitions with 75 Gb each one (in Windows drives C and D).

When I started the Ubuntu 9.10 installation, I got the partition manager screen. In this screen appears the two partitions, the first one with Windows (75 Gb) and the second one with the option to be partitioned again for Ubuntu. I selected the desired space for this partition (the basic option, side by side) and then starts the installation process. Unfortunately, my CD has some problem and the installation stops on about 25%.
Then I clicked "Install Ubuntu" again, but the Ubuntu partition created before appears in the partition manager, and I have the option to re-partitioning this "partition". I prefer do not that because I found it wrong (I think). So I erase the Ubuntu partition created before, loosing 30 Gb of space in my D drive on Windows.

In conclusion, now I have a C drive (on Windows) of 75 GB, and a D drive of 45 GB, with 30 GB lossed.

Which process I have to follow got a propper Ububtu installation in such escenary?

Bests regards

---

### Post by raymondh on 2009-11-24
> **cbustaam said:**
> Hi all, 
I've decided to install Ubuntu on my office PC. This PC has, by default, Windows XP and a hard disk of 150 Gb with two NTFS partitions with 75 Gb each one (in Windows drives C and D).

When I started the Ubuntu 9.10 installation, I got the partition manager screen. In this screen appears the two partitions, the first one with Windows (75 Gb) and the second one with the option to be partitioned again for Ubuntu. I selected the desired space for this partition (the basic option, side by side) and then starts the installation process. Unfortunately, my CD has some problem and the installation stops on about 25%.
Then I clicked "Install Ubuntu" again, but the Ubuntu partition created before appears in the partition manager, and I have the option to re-partitioning this "partition". I prefer do not that because I found it wrong (I think). So I erase the Ubuntu partition created before, loosing 30 Gb of space in my D drive on Windows.

In conclusion, now I have a C drive (on Windows) of 75 GB, and a D drive of 45 GB, with 30 GB lossed.

Which process I have to follow got a propper Ububtu installation in such escenary?

Bests regards


Hello and welcome.

Is the 30GB "unallocated".  If so, you can once again boot into ubuntu and try (in step 4) to install in "continuous unallocated space".  That will install ubuntu in the 30GB.  If not, post back.  There are other options like:

-  Use XP's disc management tool and expand D: drive and start all over
-  Create the partition beforehand and iinstruct the ubuntu installer to install unto it.  

Note that when done installing, GRUB2 will overwrite the MBR (and XP's bootloader).  Should you decide to go back to XP, you'll need an XP install disc (not the OEM supplied recovery CD's) to overwrite GRUB.

PS .... Have you tried the liveCD in live session (aka TRY UBUNTU WITHOUT ANY CHANGES) ?  Though not a thorough evaluation method, a live session gives you a chance to see how the ubuntu version plays well with your system (check wifi, sound, Fkeys, keyboard, etc, etc.).

Lastly, pls. do have a working back-up of your files.

Happy ubuntu-ing.

---

