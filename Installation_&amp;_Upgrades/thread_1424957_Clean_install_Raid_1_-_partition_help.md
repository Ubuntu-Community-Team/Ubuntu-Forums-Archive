---
title: "Clean install Raid 1 - partition help"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by stringman10 on 2010-03-08
I'm looking to set up a home file server (primary files being served are music and photos). They will need to shared between Windows and Mac PCs, so I will need to install SAMBA as well. I have two pairs of internal hard drives ( a pair of 500GB and a pair of 250GB). These are in a P3 386 box. I have created the alternate CD because I thought it would be the easiest way to set up the RAID 1. Here's my thinking of what I want the final configuration to be (looking for some help as to whether that's the right way to go and how to get there):

   - Mirror everything.
   - Use Samba to share files (possible to do non-authenticated and authenticated sharing?)
   - thinking of setting the 500GB drives as NTFS, just in case I need to move the drive
     into a windows box.

Here are my questions:

   - How should I partition the 250 GB drive that will contain the OS as well as some 
      shared files? How big should the partitions be?
   - The automatically detect option , creates /swap and targets the rest of the drive
      for /, don't think I want to do that.

I've been searching around and have found bits and pieces, but not exact answers. I would really appreciate some guidance. Thanks in advance!

---

### Post by stlsaint on 2010-03-08
> How should I partition the 250 GB drive that will contain the OS as well as some 
shared files? How big should the partitions be?


You should make enough room for the /swap, /, and a seperate partition title maybe: DATA or MUSIC/Photos...whatever you want.

---

### Post by stringman10 on 2010-03-10
> **stlsaint said:**
> You should make enough room for the /swap, /, and a seperate partition title maybe: DATA or MUSIC/Photos...whatever you want.

So here's what I did. I set a primary partition (EXT4) of 25G for /, logical partition for swap space of 1G, balance set up as logical partition EXT4, named /files2. This was on the 250 G drives (both configured identical). On the 500G drive, I set the entire drive to be FAT32 and called it /files. Both drives partitioned the same way.

Went into "Configure Software Raid" and selected the Create MD Device (RAID 1) for each partition to be mirrored, that would be / and /files2 on the 250G drive and /files on the 500 G drive. Once completed I hit finish. I received an error stating that "No root file system is defined". When I went back to the partition screen, it showed my 3 Raid 1 devices, but all of the partition types now showed raid (instead of EXT4 or FAT32) and the mount point (/, /files2, /files) were gone.

What did I do wrong?

---

