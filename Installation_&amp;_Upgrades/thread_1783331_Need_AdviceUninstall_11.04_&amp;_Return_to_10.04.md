---
title: "Need Advice:Uninstall 11.04 &amp; Return to 10.04"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by MickeyPilgrim on 2011-06-15
I dual boot with XP, My upgrade to 11.04 has been two weeks of FUBAR. I want the 10.04 LTS again.
With the 10.04 disk in, I get to the point of "Prepare Disk Space"; it shows XP-pro 81Gb and Ubuntu 11.04 75Gb. There I must choose side-by-side, Use Entire Disk, or Specify partitions Manually.
My Question/Problem> The new 11.04 kernel seems so incompatible with my system that I wonder if I need to delete or reformat. Am I likely to have success if I just tell it to do side-by-side.
Please note, I have never partitioned anything before. Please keep it simple.
MickeyPilgrim

---

### Post by alan404 on 2011-06-15
I think the way to go here is to "specify partitions manually" and then choose the partition that Ubuntu is already on - you shouldn't have to repartition, just use the one that's there, this will then delete the existing Ubuntu install. Make sure you get the right one though, obviously.

---

### Post by MickeyPilgrim on 2011-06-15
There seem to be a lot of problems with any ununstall/reinstall.
I see an article on reformatting an ubuntu partition and this seems like what that article was written for. My ubuntu partition is about 75Gb and there is a 3 GB swap partition. Together they seem to be lumped as an "Extended Partition". But you can't reformat an extended partition. All this is on   [https://help.ubuntu.com/community/HowtoPartition/ReformattingPartition](https://help.ubuntu.com/community/HowtoPartition/ReformattingPartition)

Anyone know how this should be done?  The 11.04 has been such a pile of worms that I will do anything to be certain it doesn't hang around likle a ghost.

---

### Post by guest5 on 2011-06-15
I do this quite allot it seems.  Tried and true method is to boot with gparted disk, then delete and reformat the extended partitions, both the swap and the ext3 or 4 or whichever.  

Once they are clean grub will be broken but it's ok, not to worry.

Reboot with, I prefer the alternate disks, your Ubuntu distro, and install as normal.  When you get to the partition tables simply partition them manually. Select the partition, make it usable as well as bootable, then tell the swap drive to be the swap drive and continue. 

This way you lose no hard drive space.

Oh yes, one thing, some times I have to manually add the "0" to the space before and the space after the partitions while setting them up in Gparted.  

That should do it. Works for me many times anyway.

A word about extended partitions; the hard drive only permits 4 primary partitions.  Windows can easily be 3, not leaving room for your new ext AND the desirable swap partition.  Therefore first create the extended partition, then create the two new partitions inside of that area, and now you have more than 4 partitions on one hard disk.

---

