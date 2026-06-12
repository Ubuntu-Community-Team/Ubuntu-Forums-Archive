---
title: "Installing Ubuntu on shared external hard drive"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by shwill on 2011-02-05
I have a Windows machine and a Linux machine with currently no hard drive.  I have 250 GB external USB hard drive that I use on Windows with about 50GB of files on it.  I want to install Ubuntu on it and share between Windows and Linux.  I have Ubuntu on a CD that allows me to run Linux on the Linux machine.  When I try to install Ubuntu on the external hard drive (from the Linux machine) it indicates that it will allocate about 98 GB for Ubuntu and 150 GB for files (with 50 GB of existing files).  Then it says something about partitioning something (I think) that might take a long time.  

Does this mean that Ubuntu will take up all the free space on the hard drive?

Does it also mean that when I connect the hard drive to the Windows machine, it will see two partitions when previously there was only one?

TIA

---

### Post by C.S.Cameron on 2011-02-05
If you use manual partitioning you can select whatever partition size you require. keep the first partition NTFS or FAT32, and do not format it.
Make the Ubuntu partition ext4 and Mount point = "/", You may want to leave 2GB of swap space.

Windows will not see the ext4 partition.

---

