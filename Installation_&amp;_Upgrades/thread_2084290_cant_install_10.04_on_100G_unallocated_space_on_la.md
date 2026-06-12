---
title: "cant install 10.04 on 100G unallocated space on laptop"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by LoopDLuke on 2012-11-15
Thank you in advance for your time and effort!  I have a 104G unallocated space that I made on my laptop, which runs Windows 7, by shrinking the primary drive.  Unfortunately its a HP and so there are already 4 partitions on the hard drive: system, HP tools, and recovery and the local disk.  I've looked around the forums and can't seem to make sense of how to go about it.  I'm not too computer savvy outside of how to operate windows and keep computer upkeep.  I'd installed the lucid lynx version on another laptop, where I just wiped window completely off the computer and really liked it.  That computer was accidentally destroyed not too long after i'd installed ubuntu but I heard that I should have left a small partition on the computer running windows so that I could update my HP's BIOS (It was an HP too).  If anyone can speak as to whether or not that is correct I'd like to hear their input.  Also, does Ubuntu run better in NTSF or FAT/FAT32?  Lastly, will I be able to expand the portion of my hard disk on which I am running Ubuntu?  THANKS AGAIN!!!

Luke

---

### Post by mikewhatever on 2012-11-15
Since you already have 4 primary partitions, one would have to be deleted, before you can create more for Ubuntu.

> but I heard that I should have left a small partition on the computer running windows so that I could update my HP's BIOS
What on earth do you mean by that?

>  Also, does Ubuntu run better in NTSF or FAT/FAT32?
Neither. The default file system is ext4 these days.

>  Lastly, will I be able to expand the portion of my hard disk on which I am running Ubuntu?
Theoretically, yes, but I thought you couldn't install it to the hard disk.

---

### Post by deadflowr on 2012-11-15
As mikewhatever said, you'd have to delete one of your primary partitions and then make the space into an extended partition, from there you can make multiple logical partitions.

---

