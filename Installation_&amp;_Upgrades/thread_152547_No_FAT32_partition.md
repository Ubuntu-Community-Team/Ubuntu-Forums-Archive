---
title: "No FAT32 partition"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by patanjali on 2006-03-30
I have successfully installed Ubuntu dual boot with XP Home (NTFS), but missed the opportunity to create a FAT32 partition during the install.  I believe that I need this in order to view any new files from both linux and XP.  Is this correct?
If so how do I go about creating  the FAT32 partition on my free space after the linux install?

Thanks in advance

patanjali

---

### Post by StefanoCole on 2006-03-30
You can create a FAT32 partition using GParted. If you already have the free space on the disc you can install gparted with apt or Synaptic and create the partition. If you have to shrink the Ubuntu partition to make room for the new FAT32 partititon you have to perform the operation from a live CD with a partitioning tool like GParted, QTParted or DiskDrake (see this link: [http://www.ubuntuforums.org/showthread.php?t=114142]("http://www.ubuntuforums.org/showthread.php?t=114142")).

Note: if you simply want to view the files and not edit them you can do it without the need of a new partition. From Ubuntu you can see the Win NTFS partition. In Win you can install an utility to see the Ubuntu partition. See this link: 
[http://easylinux.info/wiki/Ubuntu#How_to_read_Linux_partitions_.28ext2.2C_ext3.29_in_Windows_machine]("http://easylinux.info/wiki/Ubuntu#How_to_read_Linux_partitions_.28ext2.2C_ext3.29_in_Windows_machine")

Stefano

---

