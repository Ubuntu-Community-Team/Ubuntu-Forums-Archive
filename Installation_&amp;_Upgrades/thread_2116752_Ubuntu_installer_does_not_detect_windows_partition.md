---
title: "Ubuntu installer does not detect windows partition"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by Raptor42 on 2013-02-16
I am trying to install Ubuntu 12.10 64-bit onto a 2TB HDD that is currently entirely used by windows 7 64-bit. When I try to partition the spaces for Ubuntu, it doesn't detect ANY partitions, even when I've already partitioned it inside Windows. It just claims that there's 2TB of free space. 

Does anyone know why it might be doing this, and if there is a way of solving it?

---

### Post by darkod on 2013-02-16
First, don't create partitions for ubuntu in windows. Windows can create only ntfs and linux doesn't install on ntfs. Leave the space as unallocated (unpartitioned). Go into windows and delete these partitions.

For ubuntu not to see the partitions correctly there is usually some error in the table. For example, this often happens if the disk has gpt table and you converted it to msdos in windows. Windows doesn't delete the backup gpt table that linux can see and gets confused which table to follow.

If this is the case, fixparts run from ubuntu live mode can help remove the backup gpt table. You only need to open the disk with fixparts after you install it, and it will offer to take care of that for you.

If this is not the case, you might have another problem in the table, or the disk has raid meta data on it if it was used in fakeraid before. In this case the ubuntu installer ignores it.

To remove meta data from live mode (only if you ARE NOT running raid):
```
sudo dmraid -Er /dev/sda #(assuming the disk is sda, use the correct disk here)
```

Fixparts:
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

---

### Post by Mark Phelps on 2013-02-17
If the 2TB hard drive is just a data drive, meaning that Win7 is installed on a different drive, when you go to install Ubuntu, it would be best to have the Win7 drive disconnected.  That will ensure that GRUB doesn't actually get written to the Win7 drive and corrupt its ability to boot properly.

---

