---
title: "partition help!"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by phillychease on 2009-12-10
i had ubuntu installed using wubi but i didnt like it cuz it crashed 2 times
so i figured ill set a partition for ubuntu and install it there.
im using Paragon Partition Manager 9.5 Professional
so when i create a partition, which type do i use?
NTFS, FAT32, etc...

---

### Post by oldfred on 2009-12-10
If you are creating the partitions in advance they have to be either ext3 or ext4. The new default for Karmic 9.10 is ext4, but upgrades still keep the previous ext3.

We use gparted which you can down load as a separate liveCD or use the gparted version that is included in the Ubuntu liveCD. 

If you create the partitions in advance you have to use the manual install. Do not forget to create the swap partition of 2GB or at least as large as your memory size if you want to hibernate.

---

### Post by phillychease on 2009-12-11
> **oldfred said:**
> If you are creating the partitions in advance they have to be either ext3 or ext4. The new default for Karmic 9.10 is ext4, but upgrades still keep the previous ext3.

We use gparted which you can down load as a separate liveCD or use the gparted version that is included in the Ubuntu liveCD. 

If you create the partitions in advance you have to use the manual install. Do not forget to create the swap partition of 2GB or at least as large as your memory size if you want to hibernate.

yea i tried gparted however it only gave me the option to make the partition smaller and it max i could have was 17 mb

---

### Post by wilee-nilee on 2009-12-11
If you can get the partitioner your using to work just leave a open space for the install and choose the install in largest freespace or custom to set up the partitions. The Ubuntu installer will do the work for you.

---

