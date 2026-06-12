---
title: "Resizing Linux EXT3 partitions?"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by ubuntoexpert on 2008-03-20
I have a dual boot and I've run out of space on the Ubuntu Fiesty side due to large pictures in the /home directory.  I'd like give more space to the Ubuntu side but PartionMagic8 will not let me resize the Ext3 partions.  Can I make the partion containing the /home directories bigger without destroying data? PartionMagic shows current disk useage like this:

LocalDisk (c:)  FAT32      Size 12GB
* Unallocated               Size: 8GB
Local Disk EXT3         Size: 14GB
SWAPSPACE2         Size: 1.5GB
Local Disk EXT3        Size: 21 GB

---

### Post by forestpixie on 2008-03-20
what does this give in aterminal

df -h

Edit - try using gparted on the livecd and assuming that the partitions are next to each other you should have no problems. What windows do you have - or is it a recovery partition

---

