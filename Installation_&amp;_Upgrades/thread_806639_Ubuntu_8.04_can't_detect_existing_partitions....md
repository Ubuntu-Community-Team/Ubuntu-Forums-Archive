---
title: "Ubuntu 8.04 can't detect existing partitions..."
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2008-05-25
Ubuntu 8.04 can't detect existing partitions


I downloaded the "Ubuntu 8.04 LTS Desktop Edition", but only get two options for partitions during installation.

"
Prepare disk space

How do you want to partition the disk?

Guided - use entire disk

SCSI1(0,0,0)(sda) - 120.0GB ATA Hitachi HTS54121

Manual
"

If I select "Manual", I got only one Device "/dev/sda".

However, if I try "sudo fdisk -l" in bash, what I've got is:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7650    61447601    7  HPFS/NTFS
/dev/sda2            7650       14406    54272000   83  Linux
/dev/sda3           14407       14593     1502077+  82  Linux swap / Solaris


As you can see, I do have a Linux partition(for Ubuntu 7.10) and a Swap partition. It's for sure I won't remove my Vista NTFS partition, just in order to install Ubuntu 8.04 . It's pretty strange that Ubuntu 7.10 works fine with my partitions but Ubuntu 8.04 doesn't work at all.

Is there a fixed version for this Ubuntu 8.04 release? 



Best Regards
JIA Pei

---

### Post by seventhguardian on 2008-11-14
Hello,

I'm also experiencing this problem. I was forced to use the "minimal CD" because of some strange errors with the normal installation procedure.

This is an "old" Pentium 4 desktop PC, and I suspect there's some problem with the IDE/SATA controller.

My advice, and what I'll do next (as soon as I finish burning the cd) is to install the 7.10 version and then upgrade.
EDIT: It didn't work. 7.10 still doesn't detect my partitions...

---

### Post by seventhguardian on 2008-11-14
Problem solved.

I've tried opening the disk with "parted", and it complained about overlapping partitions! So after solving this overlaping (I have no idea on how they overlapped in the first place) everything went ok.

Looking at your fdisk data this also seems to be your problem:

Device Boot Start End Blocks Id System
/dev/sda1 * 1 7650 61447601 7 HPFS/NTFS
/dev/sda2 7650 14406 54272000 83 Linux
/dev/sda3 14407 14593 1502077+ 82 Linux swap / Solaris

You have sda1 and sda2 overlapped: sda1 ends with block 7650 and sda2 also begins with this block. It should begin with block 7651!

I hope this helps.
Cheers,
  Renato

---

