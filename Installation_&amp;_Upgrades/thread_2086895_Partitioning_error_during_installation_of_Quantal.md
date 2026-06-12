---
title: "Partitioning error during installation of Quantal"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by lukThe2nd on 2012-11-22
Hello,

during installation of the latest Kubuntu (Quantal, 64bit) on my Thinkpad T420, the following problem araised:

The live system can be started and runs without any problems. However, if I want to install the system on the hard drive, I have no choices in the partitioning section (The container is totally blank). The funny thing is that I can access all partitions (Windows 7 and recovery) in live mode.

The output of "sudo fdisk -l" is the following:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1badcb5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     2457944     1228941    7  HPFS/NTFS/exFAT
/dev/sda2   *     2457945   166304879    81923467+   7  HPFS/NTFS/exFAT
/dev/sda3       954759015   976771119    11006052+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2088 MB, 2088763392 bytes
65 heads, 62 sectors/track, 1012 cylinders, total 4079616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014994

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     4078359     2039149    c  W95 FAT32 (LBA)

```

Thanks in advance

Lukas

---

### Post by nothingspecial on 2012-11-22
Changed title to reflect the question.

---

### Post by oldfred on 2012-11-23
Do not know partition tools in Kubuntu. 

I always use gparted and partition in advance. Gparted also may show if a NTFS partition has issues and needs chkdsk run.

       
[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

    
I have had, in older versions where my XP booted, but gparted would not even show entire drive. Once I ran chkdsk then XP booted faster and gparted showed my sda drive. Now I think gparted just shows warning icons - yellow or red next to partitions with issues and clicking on icon may give more info on issue.

---

