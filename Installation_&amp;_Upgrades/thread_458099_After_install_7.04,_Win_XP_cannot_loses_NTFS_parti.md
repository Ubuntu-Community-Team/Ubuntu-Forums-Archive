---
title: "After install 7.04, Win XP cannot loses NTFS partition"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by 4WoofGrrrr on 2007-05-29
Please help me if you can.


I just installed Ubuntu 7.04 on my existing Win XP system in an attempt to make dual-boot system.

The system has two hard drives, one is SATA and the other is EIDE.

The SATA drive has two FAT32 and one NTFS partition.  Win XP is installed on the NTFS partition.
The EIDE  drive had one NTFS partition and lots of free space

I installed Ubuntu from the Live CD on the EIDE drive.

When it was time to assign partitions, I create a SWAP and several REISERFS partitions:
        /    /var    /usr    /opt    /home
The install completed and Ubuntu booted from the hard drive with no problems.



When I tried to reboot, however, I got booted directly into Win XP!!!  No option to boot Ubuntu.
No menu.  Just directly to Win XP.

I figured out that the Ubuntu install put the MBR on the EIDE drive, NOT the SATA drive,
and my BIOS was setup to boot the SATA drive.  So I used GRUB from the SuperGrub
CD to write the MBR on the SATA drive.  It worked.  The boot menu showed up!



Everything was fine.

That is, until I noticed one of my Win XP drive letters was missing!!!  An NTFS parition
on the same EIDE drive onto which I installed Ubuntu is missing.



I bring up Win XP Disk Manager, and the EIDE drive is not even listed.  The whole drive
has just vanished, along with the NTFS partition on it.  No linux partitions.  No free space.
Notning.

I bring up the Win XP Device Manager, and the EIDE drive is there.  I display its properties
and click the "Volumes" tab, no partitons are displayed.  When I click the "populate" button
NOTHING IS DISPLAYED.

When I boot Ubuntu, the NTFS filesystem is there.  I can read files from it.  All the paritions
I created during the Ubuntu install are there as well!



So what happened?  Did "parted" during the Ubuntu install write a Partition Table that
Win XP doesn't understand???   If so, can I make it write a Partition Table that Win XP
DOES understand?  How?   Is there any way to fix this?



Thanks for any help you can provide.

---

### Post by LaRoza on 2007-05-29
-edit Sorry I did not read entire post, my understanding of the question was not complete.

---

### Post by 4WoofGrrrr on 2007-05-31
I solved this myself.

I completely re-partitioned the drive and re-installed everything.

It all appears to be fine now.

---

