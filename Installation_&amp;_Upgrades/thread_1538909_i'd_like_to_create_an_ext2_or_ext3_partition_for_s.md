---
title: "i'd like to create an ext2 or ext3 partition for storage"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2010-07-25
currently running windows because ubuntu has proved to be unstable on my new machine.

i am accustomed to having a partition on the second physical disc to put my clonezilla backups there. i normally use NTFS for that partition (on my previous machine, no problems). after i created the new partition i wanted, formatted it (full format, not quick), then started clonezilla, it doesn't show me that partition with it's size. it just shows me the partition on the disk with no size, and the partition listed above it is of the same disc, but with it's full capacity listed.

so i have 2 drives on my system:
intel 80GB SSD
toshiba 320GB HDD

the intel has 2 partitions on it, those are listed fine
the toshiba also has 2 partitions on it, one of the items listed shows it 320GB, the other doesn't list a size.

not sure why it's doing this, but it's kicking back insufficient space errors when i try to backup my intel windows install, probably because it's not registering properly with clonezilla.

so i'd like to try another FS, like ext2 or ext3. but i want to know how to specify the partition properly (what mount point, etc.) i'll be using gparted live to do this ...

---

### Post by theozzlives on 2010-07-25
With an ext2 or ext3 you can't access it Windows. Unless you install ef2fs to access your partition.

---

### Post by zero7404 on 2010-07-25
> **theozzlives said:**
> With an ext2 or ext3 you can't access it Windows. Unless you install ef2fs to access your partition.

don't need access in windows. in fact i want to do ext2 or ext3 in order to isolate from the windows read/write system ...

---

