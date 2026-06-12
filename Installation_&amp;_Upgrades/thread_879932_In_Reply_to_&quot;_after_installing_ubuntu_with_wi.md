---
title: "In Reply to &quot; after installing ubuntu with windows xp disk geometry problem&quot;"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by KramerLee on 2008-08-04
This was a post from March this year, which is in archives so it can't be replied to directly.  It was:

[http://ubuntuforums.org/showthread.php?t=722176](http://ubuntuforums.org/showthread.php?t=722176)

It was posted Kai111

I have run into this same "problem."  At least some Compaq, Lenovo, IBM, and other computers have BIOSes that work with hard drives giving them a 240 head geometry parameter.  In most other computers the same hard drives would be given the geometry parameter of 255 heads.  

Linux is apparently not concerned with this chosen geometry, and assumes 255 heads on its partitions, leaving the other partitions with their BIOS given 240 head geometry, at least on teh computers I have worked with.  

This seems to only a problem if we try to use PartitionMagic, DriveImage or DriveCopy, (and maybe some other disk copying software) as they just give dire warnings about partition table errors and stop before they can do their intended functions.  Gparted has to work even if there are these inconsistencies in the secondary partition tables, and if PowerQuest was still around, its products would probably have been modified to take this into account.

My experience with this is:

I have a compaq computer which gives them the 240 head geometry in the partition tables.  I can even set up the Linux partitions with PartitionMagic and they will show the 240 head geometry.  Then, no matter the Linux distro, if I install Linux, even using the pre-made EXT3 and SWAP partitions, made with PartitionMagic, after the install the linux-related partitions now have 255 head geometry, and PartitionMagic chokes.  If I remove all Linux partitions, then PartitionMagic thinks it is fine, as it has only the 240 head geometry left, everything is OK.  

By the way, this difference in 240 heads verses 255 heads (or whatever number) is a problem as far as Windows is concerned.  Windows will just not work if you take a drive from a machine that formatted it with the 240 head geometry and put it in a machine that uses the 255 head geometry (or vice versa).  Linux doesn't care what the BIOS thinks the geometry should be, it just talks directly to the disk and likes to use 255 head geometry.  

It all works together fine with 240 head Windows partitions and 255 head Linux partitions.  It is just that PartitionMagic is not made to deal with that, and PowerQuest has been bought by Symantec and no more work is being done on PowerQuest products that I can find anyway.  

GParted seems to be fine with this change in geometry, so I guess we have to use that.  Gparted maybe be the program that used that geometry during the Linux install process.

If your computer uses the 255 head formatting geometry, then PartitionMagic works fine as the geometry is consistent all through the main partition table and the extended partition tables.  This is not an Ubuntu effect, it is a Linux effect verses Windows, because Windows uses the BIOS value and Linux uses its own value.  Just about any Linux version works this way.  Apparently in designing GParted they decided it is better or easier to just do all Linux partitions using 255 head geometry whether or not the Windows partitions were made with 240 head geometry or even some other geometry.

---

