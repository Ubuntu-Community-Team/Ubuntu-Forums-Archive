---
title: "Problem creating fat32 partition during install"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by futui tuam matrem on 2010-06-28
Hello all,

Sorry if this has been addressed, I've looked and can't find an answer anywhere.

I purchased a new HD and my goal is to have a Windows partition, an Ubuntu partition, (a swap partition of course), and large fat32 partition for storing data to be used on both the Windows and the Ubuntu side.

I am installing from USB and do not yet have a copy of Windows to install. I keep getting an error saying that the attempt to mount vfat failed.

If anyone has advice on how to fix this, or an easier way to create a shared data partition, I would really appreciate it.

Thanks

---

### Post by C.S.Cameron on 2010-06-28
I would suggest the procedure would be to use manual partitioning during the install procedure.
First partition would be NTFS, Primary, Beginning, Windows.
Second partition, FAT32, Primary, Beginning, Windows.
Third partition, ext4, Primary, Beginning, /.
Fourth, Swap Area, Beginning.
Windows might prefer the second partition to also be NTFS.

---

### Post by futui tuam matrem on 2010-06-28
Thanks for the advice. I am using manual partitioning and NTFS is not one of the options included. I have just been choosing to leave the first partition empty for now as I do not yet have a Windows installer. Other than that, I am doing exactly as you suggested. Every time it refuses to create the FAT32 partition.

---

### Post by futui tuam matrem on 2010-06-28
Shameless bump. It seems hard to believe that this isn't an easily solved problem. Why cant 10.4 format FAT32 for me?

---

### Post by oldfred on 2010-06-28
You may want to rethink FAT if you are storing large files.

NTFS and Fat info:
FAT 4GB max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)


The installer does not have the extra tools to do windows formats since it is installing Ubuntu. I always have created & formated partitions in advance so it is a non issue for me.

---

### Post by aphatak on 2010-06-28
I would leave the first partition as 'unused' till you can install Windows on it.
Also, if the sole reason you are not installing NTFS is that you are not offered the option, try 'sudo apt-get install ntfs-progs', and then using gparted to format the partition.  I would much rather have an NTFS partition than a VFAT one.

---

### Post by futui tuam matrem on 2010-06-28
Thank you! ntfs-progs did the trick. Marking as solved.

---

