---
title: "Disk alignment on new install"
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by mark allyn on 2015-08-20
Hello everyone,

I recently attempted to install 14.04 from a CD to a 2 TB external Seagate drive.  In doing so, I encountered an error message similar to the following:

  "The partition /dev/sdb1  assigned to / starts at an offset 2560 bytes from from the minimum alignment for this disk, which may lead to 
   very poor performance"

The message also invites me to go back and erase the original partition and then create it again, promising that this will fix the problem.  This doesn't work.  Hitting the "continue" button simply causes the message to be repeated.

What is going on here?  I've not run into this problem in previous installations on external drives.  How to fix?

Thanks,
Mark Allyn

---

### Post by oldfred on 2015-08-20
All new partition tools from both Windows & Linux partition correctly. Did you use some very old tool to create partitions.

Larger drives are often gpt partitioned, but 2TB is the limit on the 35 year old MBR(msdos) partitioning, so you may still have MBR.

Post this to see sectors:
        sudo parted /dev/sdb unit s print

    
 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by mark allyn on 2015-08-21
Hi OldFred,

Thanks for helping.  The external drive is 2 TB, but it has a MBR, not GPT table.  i partitioned it using the partition tool that comes with the install disk, so I was surprised when it ran into trouble.  I have managed to two partitions, / and swap, and installed U14.04.2 on them, but third or fourth partitions are still misaligned.  The installation runs fine, but I'd like to be able to do two more partitions.

I'm trying to do the alignment using fdisk (not gdisk).  I'm fuzzy on this business of 512 byte sectors vs. 4096.  I seem to be using tradtitional 512 sectors for physical/logical sector size.

I looked over the material you flagged.  Good stuff.  Thanks.

Mark Allyn

---

### Post by mark allyn on 2015-08-21
Hi again, OldFred,

I take it back.  Just checked again.  The size is 512B/4096B (logical/physical).  The patition table is MBR.  Got that part right.

Mark

---

### Post by oldfred on 2015-08-21
The extended partition may be flagged as not in alignment, but that does not matter as you cannot write to the extended partition, only the logical partitions inside the extended.

I have only used gpt for all new drives since version 10.10. Cannot say I really notice any difference but that is a good thing as it has just worked.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

If at some point you are going to get a new UEFI system, then better to start using gpt as better to have all drives as gpt. But Windows only boots in UEFI mode from gpt drives, so if an internal drive and you want Windows in BIOS mode you must stay with MBR.

---

### Post by mark allyn on 2015-08-22
Good morning, OldFred,

There are only two partitions on the external drive:  / and "swap".  The rest is unallocated as of this time.  It is the unallocated chunk that is misaligned.  I am unclear in your last post about your reference to "extended partition".

Thanks for sharing the threads.  They are generally very useful.

Regards,
Mark

---

### Post by dino99 on 2015-08-22
Try to get the Seagate tool to boot with, an check the partitions. Is that hdd still have jumpers ? what the doc say ?

---

### Post by oldfred on 2015-08-22
Post this to see alignment:
       sudo parted /dev/sda unit s print

---

### Post by mark allyn on 2015-08-23
Dino99 and OldFred-

Dino:  no jumper.  What Seagate tool do you have in mind?

OldFred: used parted command you suggest.  The first partition starts 4096B in.  This partition is / and is ext4 filesystem.  The next partition is "swap" and it is not on a 4096 boundary (the start is not divisible by 8).  My understanding from looking into this is that swap doesn't need to start on a physical block--got this from the IBM paper you pointed out).  The third partition (another primary) would need to be located at a 4096 boundary if it is any of the Linux filesystems.  Also from my reading, GPARTED (with MiB switch"on") would do the job correctly.  I'll have to try this.

Mark

---

### Post by oldfred on 2015-08-23
I normally try to keep swap at end of drive with MBR and in an extended partition, so I have to opportunity to resize without having to change swap around. 
But since I convert to gpt partitioning I have not done that for ages.

---

