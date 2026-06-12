---
title: "partition table problem,"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by musa-ktk on 2011-12-18
Hi helpers :(,
        I am facing a bizarre problem. I have installed standalone Ubuntu 11.10 on my PC, and was working fine until i decided to install Windows 2008 R2 for testing purpose alongside with Ubuntu.
        Before installing Windows 2008, my partition table  was something like this:

**/dev/sda1**   primary partition (40 GB mounted on** /**,  on which Ubuntu lies)
**/dev/sda5 **                             (30 GB ext4 , mounted on **/home**)
**/dev/sda6 **                             (70 GB NTFS, mounted **/media/general**)
**/dev/sda7 **                             (75 GBNTFS, mounted **/media/others**)
**/dev/sda8**                              (80 GBNTFS, mounted **/media/videos**) 

I wanted to install Windows on **/dev/sda7**, but as it was not primary partition, i could not. so from windows interface i tried to delete it but it stuck there. so i just restarted the system.( which is causing me all this problem)

now when i start Ubuntu, screen goes black, and after a brief pause it prints **KILLED** on top left. (nothing else)
i selected recovery mode from GRUB menu, it loads some files then stops, saying kernel memroy error, no killable processes.

i booted form Flash drive with Ubuntu Live, here is the queer result of _**fdisk -l**_ in terminal

Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf305bc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29295616   83  Linux
/dev/sda2            3648       36481   263735969+   f  W95 Ext'd (LBA)
/dev/sda5            8288       17465    73722253+   7  HPFS/NTFS
/dev/sda6            8288       17465    73722253+   7  HPFS/NTFS
/dev/sda7            8288       17465    73722253+   7  HPFS/NTFS
/dev/sda8            8288       17465    73722253+   7  HPFS/NTFS
/dev/sda9            8288       17465    73722253+   7  HPFS/NTFS
/dev/sda10           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda11           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda12           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda13           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda14           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda15           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda16           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda17           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda18           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda19           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda20           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda21           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda22           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda23           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda24           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda25           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda26           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda27           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda28           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda29           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda30           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda31           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda32           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda33           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda34           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda35           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda36           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda37           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda38           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda39           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda40           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda41           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda42           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda43           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda44           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda45           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda46           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda47           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda48           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda49           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda50           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda51           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda52           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda53           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda54           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda55           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda56           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda57           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda58           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda59           8288       17465    73722253+   7  HPFS/NTFS
/dev/sda60           8288       17465    73722253+   7  HPFS/NTFS


well, I have got no idea how they came into being, ostensibly they look like copies of each other having same data as i had on** /dev/sda6** (/media/others)
and i cant find my data that resided on **/dev/sda8** (/media/videos), i dont want to lose all the data i had on that partition, and I have no idea what to do next.

Help is required desperately.

---

### Post by xyzzyman on 2011-12-18
Well it seems you have more than 60 partitions. But from what's shown they all have the same start/stop which is why they are duplicates? Maybe gparted will show more than 60?

---

### Post by musa-ktk on 2011-12-18
Thanks for reply

well, gparted shows less actually,, it shows the correct no. of partitions that i had before,, but only /dev/sda5 seems to be functioning ,, others are marked as unallocated :( 

It seems like the partition table is corrupted,, is there anyway to just fix the partition table? or i have to re-format every thing (which is last thing i would do).

or any other way to get back my data easily ( lets not talk about data recovery softwares).

---

### Post by darkod on 2011-12-18
From live mode you can scan the disk with Testdisk and see what partitions it finds. If it can recognize them correctly, you can write the partition table.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And just for future reference, I don't understand the plan to delete sda7 to try and create primary in its place. If its physical location is really between sda6 and sda8 you can't create primary in the middle of your extended partition. Because that would split the extended and only one extended is allowed, not two.

---

### Post by musa-ktk on 2011-12-23
> **darkod said:**
> From live mode you can scan the disk with Testdisk and see what partitions it finds. If it can recognize them correctly, you can write the partition table.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And just for future reference, I don't understand the plan to delete sda7 to try and create primary in its place. If its physical location is really between sda6 and sda8 you can't create primary in the middle of your extended partition. Because that would split the extended and only one extended is allowed, not two.
Thanks darkod, i found about Testdisk later when i decided to finally re-partition and run data recovery afterwards, which i did but could not recover most of it. Thanks anyway.

And yes, it was futile to delete extended partition at first, I guess i was just curious to see what happens(was not good experience at all).

---

