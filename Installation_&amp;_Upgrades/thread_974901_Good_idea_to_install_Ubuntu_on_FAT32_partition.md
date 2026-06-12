---
title: "Good idea to install Ubuntu on FAT32 partition?"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by andrewwg94 on 2008-11-07
because that way windows can access ubuntu easily without the ext2 driver. i don't see any cons.

---

### Post by crwmike on 2008-11-08
FAT32 does not support file permissions.

If you want to access Ubuntu from Windows, install Ext2 IFS.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ad_267 on 2008-11-08
That wouldn't work at all. If you don't want to install the ext2/3 driver you could have a separate ntfs or fat32 data partition.

---

### Post by FrostyFlames on 2008-11-08
Another idea would be to create another partition that is FAT32 and use it as a transfer area or commmonplace to store data between the two operating systems.

---

### Post by dirgaizan on 2012-06-18
I suppose if a partition c, d and e, I want to install ubuntu in c and c in the format the partition to ext4 and the rest is fat32, if it's not what happened?

---

### Post by jmore9 on 2012-06-18
I have been using winxp on my other machines for a while now.  I have converted all but one , the one that runs the tv to linux.  They all have EXT4 parts , except for one drive which is still NTFS just so i can transfer stuff back and forth.

I haven't really had any issues with using NTFS with ubuntu , fedora , opensuse , linuxmint at all.  And at one time all drives except the boot/root where all NTFS.  I only changed everything because NTFS is Microsoft and it is private and linux has its own partitioning formats.

In my opinion if you have no need for windows machine to talk to linux machine you should use linux parts.  If you have some windows machines maybe just use one for them to talk to , keep others in linux format.

---

### Post by coffeecat on 2012-06-18
Ancient thread - closed for necromancy.

The OP's question was answered long ago. You cannot install Ubuntu on a FAT32 partition. If anyone needs help with setting up partitions to be shared between Ubuntu and Windows - which is a separate matter - please start a new thread.

---

