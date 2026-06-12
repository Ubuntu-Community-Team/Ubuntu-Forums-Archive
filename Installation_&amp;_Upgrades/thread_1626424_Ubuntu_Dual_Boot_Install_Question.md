---
title: "Ubuntu Dual Boot Install Question"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by mhammann57 on 2010-11-20
Hello,
 
I want to install Ubuntu 10.04 on an XP system (NTFS) so that Ubuntu runs from a FAT32 partition. Once I set the slider to give XP 750GB and Ubuntu 250 GB it looks like Ubuntu will use the ext4 filesystem which XP can't see. Will I be given the option to select FAT32 for the Ubuntu partition if I continue? If not, is there a step by step guide for this?
 
Thanks,
 
Mark

---

### Post by Quackers on 2010-11-20
Ubuntu's default file system is now ext4 although ext3 can be used afaik. It will not run on a fat32 formatted partition.
Speaking of partitions, have you already made one for Ubuntu or are you trying to create the space from the XP partition while you are installing? This is not a recommended way, if you are. It could have a serious risk of data/system loss for XP.
If you need to resize your XP partition in order to make space for Ubuntu I would suggest that you defrag XP at least twice and then shrink the XP partition using Windows tools only.
Ubuntu can then be installed into the resulting free space using the manual partitioning selection during installation.

---

### Post by oldfred on 2010-11-20
I do not recommend FAT32 for anything except where you have to use it on external cards for compatibility with your camera or phone. It is ok for partitions below 4GB, but larger partitions should be NTFS as they are journalized and then can be repaired easily. Files over 4GB copied to FAT are truncated and in effect destroyed. 

Unless you install with wubi inside a windows partition you have to use Linux type partitions not windows types. Part of this is the advantage of security and safety in Linux as the files system has permissions and ownership that windows does not.

---

### Post by mhammann57 on 2010-11-20
OK, Thanks!  You probably saved me a giant headache.  I think I will get a second drive and install it there instead of messing with partitioning of the disk with XP. 
 
Thanks Again!
 
Mark

---

