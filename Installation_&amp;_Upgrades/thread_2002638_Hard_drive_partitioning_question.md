---
title: "Hard drive partitioning question"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by Rebootin on 2012-06-12
Hi all,

I have a HD partitioning issue. I am trying to install Ubuntu 12.04 as a dual boot OS with WIN 7 (home premium). This is on a HP Pavilion dv6 notebook, x64 based, Intel i3 cpu 2266 Mhz, 2 cores\4 logical processors. 4 gigs of memory.

My problem is the HD allows 4 primary partitions. These partitions are already factory defined:
System – 199 MB NTFS - PRIMARY
C: - Windows – 238.53 GB NTFS - PRIMARY
Unallocated – 213.53 GB
D: - Recovery – 13.12 GB NTFS - PRIMARY
E: - HP_Tools – 103 MB FAT32 – PRIMARY

I was planning on using the Unallocated space for Ubuntu and Storage. It seemed so simple! Then I learn the drive can only have 4 primary partitions.  &#61516;

I’m open for suggestions …… please?

---

### Post by madverb on 2012-06-12
Backup HP_Tools partition. Wipe partition. Create an extended partition in the 213.53 GB unallocated space. Then you can create as many logical partitions in there as you like.

more info: [http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/HP-TOOLS-partition-could-be-backup-to-image-then-restore-on-a/td-p/1469819](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/HP-TOOLS-partition-could-be-backup-to-image-then-restore-on-a/td-p/1469819)

---

### Post by darkod on 2012-06-13
Slight difference. I wouldn't create any extended partition from windows. After you delete HP_TOOLS leave the space as unallocated, as it is.

Start the ubuntu installer and it will create the partitions as logical anyway. Doesn't matter if you use one of the auto methods or manual partitioning.

---

