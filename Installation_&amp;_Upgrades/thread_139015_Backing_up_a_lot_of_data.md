---
title: "Backing up a lot of data"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by IYY on 2006-03-03
I have some 50 GB of movies and music on my XP computer, stored on an 80 GB harddrive. I need to do a fresh install of Windows, and would also like to make an Ubuntu partition. However, I don't have a DVD burner, and none of my other computers have enough disk space for a backup. 

What I plan on doing is buying a new ~100GB drive, which I need anyway, somehow copying all my files on it, and then do the format. 

I'm not very good with partitioning, though, and am afraid to lose my data. Could anybody suggest a more detailed, step by step plan?

---

### Post by aysiu on 2006-03-03
If you buy that external hard drive and back up your data, it won't matter if you lose it, right?

That said, this dual boot guide will tell you everything you need to know to safely repartition and install Ubuntu:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by akiro.yamamoto on 2006-03-03
When you get your 100GB drive, add it as a Slave on the 1st IDE or Master on the 2nd IDE.
Now if you Ubuntu already installed on your Master IDE1 chain. Install gParted from the repos. Use gParted to create/format a 100GB ext3 partition on the newly attatched drive. Then backup your files to the new partition.
If Ubuntu is not installed, you can use the live cd to create/format the partition on the 100GB drive. Then backup your files.
Once your done. 
Use your Win Install CD to erase the partitions on your Master Ide1 drive. Then create one (1) 35GB NTFS or FAT32 Partition, install M$ Win to that partition.
When your done.
Use your Ubuntu Install Cd to create a 44.5 GB Reiserfs Partition and a 500MB Swap partion. Install Ubuntu to the 44.5 GB partition and complete the install.
Note: You can add a mount point for the 100 GB partition  during this install process.
You should have something as follows:
/dev/hda1    NTFS    35GB    (Windows)     mount point => /media/win_c
/dev/hda2    Reiserfs 44.5GB  (ubuntu)     mount point => /
/dev/hda3    SWAP    500MB   (swap)        mount point => none
/dev/hdb1    EXT3    100GB    (Backup)    mount point => /media/backup
/dev/hdc      CD/DVD CD/DVD  (CD/DVD) mount point => /media/cdrom0

Now you may be wondering why I told you to format the 100GB partition as ext3
well there is a driver for Win that allows it to be used under M$ Win. and it will not
have the size restrictions of the Fat32 file structure.
You cannot have a file greater than 1gb on Fat32 (no DVD ISO files)  but you can 
under ext3.
So Google for the Ext driver for Win, install it and you will be able to read and write
to your 100GB EXT3 partition easily.
I hope this general outline helps you out. Feel free to modify as you see fit, after
all it's not like it's writen in stone. ;)

---

### Post by aysiu on 2006-03-03
[QUOTE=akiro.yamamoto]
You cannot have a file greater than 1gb on Fat32 (no DVD ISO files)  but you can 
under ext3.[/QUOTE] FAT32 does have a file size restriction, but it's actually files no bigger than *4* GB, not *1*.

---

