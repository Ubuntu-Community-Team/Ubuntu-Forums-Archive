---
title: "HDD space management during Installation"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by pra23 on 2015-09-30
Hi,
I decided to go with linux over windows on my 2 year old desktop.I am gonna go with either Linux Mint 17.2 Cinnamon or Ubuntu 14.04 Lts. I have not decided on that yet. I am looking for a guideline about HDD management during Installation. On that time it is asked "This computer currently has no OS detected. What would you like to do ?" 
I went over various forums (and few Youtube Videos) and they suggested that I should select "do something else" because it let your handle HDD space better.What I got from the discussion is
1. do the partition the drive with 50 GB (more or less) of spaces for OS (with mounting point '/' ) [ primary partition]
2. a few GB of swap area because of my limited RAM in machine. [ primary partition ]
3. leave the rest for Home folder. [ primary partition ] 
What it will do for me when i would like to try a different version of linux later on it will keep my data unchanged on my home folder.
Here comes my concern:
I have 1 TB HDD. When I was on windows 7 I used almost 100 GB of it for :C drive. Of the rest of spaces I broke it to two partitions - one for the important stuffs other for multimedia files.In the benefit of this configuration, when my windows 7 crashed (which used to happen once in 6-7 months), i installed a fresh windows 7 on drive C and my rest of files remains intact. In linux, we have Home folder to take care if that kind of problem happens. But for my case almost 850 GB of home folder is bit of too much space for a drive and it will hard for me finding or categorize a file on such broad space.
So i wanted to go with my windows like configuration i.e. 1. 50 GB of OS 2. 4 GB of swap spaces 3. 150 GB of Home and 4. rest of it broken into 2 parts as said earlier. Then i found out that linux does not allow you 5 primary partition for a single drive. So have to go for Logical Partition. If I do that and someday i want to change linux distro then will the files in logical drives still can remain intact ? And 5 partition for a HDD will effect the performance of my PC?

P.s. Please try on to laugh at my stupid question.

---

### Post by sudodus on 2015-09-30
Welcome to the Ubuntu Forums :-)

If you want to go with a classical MSDOS partition table, you can have only four primary partitions, but there is no effect on performance to use an extended partition, and inside that partition you can have a lot of logical partitions.

But install Windows into a primary partition, if you decide to dual boot. The rest of the drive can be an extended partition (and inside that you can have a common data partition with the NTFS file system. On the other hand, if you only have linux, it is better to have a data partition with the ext4 file system. If you run the Ubuntu installer in BIOS mode, it will install Ubuntu for BIOS mode.

If you want to go with the newer GUID partition table, GPT, you can have many partitions. You need no extended partition. If you want to boot it from BIOS, you need a small (1 MB) partition without any file system, but with the bios_grub flag. The GUID partition table is also necessary if you want partitions larger than 2 TB.

If you want to boot an installed system from UEFI, you need the GUID partition table. If you run the Ubuntu installer in UEFI mode, it will install Ubuntu for UEFI mode.

---

### Post by oldfred on 2015-09-30
With my older BIOS only system I started converting to gpt on newer drives. But if you later want Windows you have to have a UEFI system. Windows only boots from gpt partitioned drive with UEFI. Ubuntu can use BIOS or UEFI from gpt.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

With my BIOS system I had many 25GB / (root) partitions. I keep one LTS version as main working install. I left space unallocated and kept adding 25GB / as I had the room. I had a 100GB for data, smaller partition for backup of /home. I did keep /home inside / and put all data folders from /home in my data partition so every install could use the same data. Most of the partitions were logical as my large drive was configured for MBR(msdos), just before I started converting drives to gpt and did not want to convert it.

My new last year UEFI system is somewhat similar. But I have a small SSD for / (or two) and data on HDD. My data partition and several newer test installs are now on HDD with still lots of unallocated space. Both drives are gpt as required by UEFI.

---

### Post by ubfan1 on 2015-09-30
+1 on oldfred's setup.  I recently found I really needed a FAT partition for testing new iso releases booting from the hard disk.  Not that the iso needs FAT, but I like to have persistence in such cases, and I found (contrary to some docs), that the persistence files only work when on FAT filesystems.  I set up 10G partition, put a vfat filesystem on it, and have directories A, B, C, D,... for my persistence files for different iso boots.  I select the persistence file with the "persistence-path=/A" after the word persistence on the kernel boot line (again, contrary to some docs which say you don't need the word "persistence" if you use "persistence-path").  The EFI partition is FAT, but too small to hold a 1G file.

---

### Post by Dennis N on 2015-09-30
> Then i found out that linux does not allow you 5 primary partition for a single drive. So have to go for Logical Partition. If I do that and someday i want to change linux distro then will the files in logical drives still can remain intact ? And 5 partition for a HDD will effect the performance of my PC?

I now always use GPT disk partitioning which have by default 128 partitions. There are no extended and logical partitons to think about. The partition table has redundancy - there is a backup kept. I keep personal files off of the OS partitions in a separate one so they can be shared with the other Linux OSes on my machine. That partition will not be touched by any installation process. With a new OS, all I need to do is set it up to be mounted.

There is no observable performance degradation with five or more partitions. Only a couple are usually mounted. 

Also, there is no Windows installation on any of my computers. That seems to be the root of most problems.

---

