---
title: "repartitioning hybrid hard drives (ssd+hdd)"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by gonzobilbao on 2012-10-05
Hi everyone


I installed recently Ubuntu on my new laptop, an hp envy 4 1050ca; I shrank my windows partition and created some unalocated space, both in my hdd and my sdd and installed ubuntu succesfully after braking the RAID configuration tha links both drives. But I installed ubuntu accidentally only on my hdd, whereas my intention was to install the booting files in my sdd for fastness and use the unalocated space in my hdd for storage. How can I correct  this? Should I delete my ext3 partition and try a fresh, custom installation?

Thanks for your help!!
Gon

---

### Post by oldfred on 2012-10-06
If it is seen as a separate drive, it probably would be easier to just reinstall. Settings for a SSD should be somewhat different than for a Hard drive install. You can keep /home or data partition(s) on the rotating drive.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

---

### Post by gonzobilbao on 2012-10-06
Thanks oldfred! and how shoul I get started? Should I delete my Ubuntu partitions from Windows or with Gparted from a live usb? 

Cheers

---

### Post by oldfred on 2012-10-06
I would use gparted for anything Linux. Windows does not really see Linux partitions and often messes up partition tables when it tries to delete them.

---

### Post by gonzobilbao on 2012-10-06
awesome, i'll post the outcome when i'm done so more people with the same problem can know

Cheers!

---

### Post by gonzobilbao on 2013-02-08
I finally made it. I got / on the SSD and /home and swap on the HDD, in the same extended partition, sharing the drive with windows.Pretty smooth and now, super fast!! I am satisfied with the performance of my computer now. I was thinking of moving swap to the ssd, but apparently this might decrease the life span of the ssd drive... so I dont know what I'll do, for the moment i am alright!

Cheers!:popcorn:

---

### Post by Kixtosh on 2013-02-08
I followed that link posted earlier by oldfred myself, since I've been using Ubuntu on a SSD only system for two or three years already, and I'm about to set up a couple more as well. I was interested in the question about swap, and here's what I found:

> One can place a swap partition on an SSD. Note that most modern desktops  with an excess of 2 Gigs of memory rarely use swap at all. ...[https://wiki.archlinux.org/index.php/Solid_State_Drives#Swap_Space_on_SSDs](https://wiki.archlinux.org/index.php/Solid_State_Drives#Swap_Space_on_SSDs)

Since my system is an ultraportable laptop with RAM limited to a maximum of 2.0 GiB, I set swap at 2.1 GB (mostly so that I could use the hibernation mode of standby without errors). I can confirm that every time I check with the System Monitor, it is very rare indeed for the system to be using any swap at all. I would conclude that there's no need to be paranoid about it in the short term at least. Perhaps there is a tool that would allow some sort of log of swap usage, but I don't know of one, or I'd post my results for you.

---

