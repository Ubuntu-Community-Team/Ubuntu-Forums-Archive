---
title: "Problem in Installing Xubuntu 11.04 along Windows 7"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by pri1728 on 2011-10-25
Hello,

I am new to Linux. I want to install Xubuntu 11.04 (or a more stable version) along Windows 7 which is already running on my laptop (Dell XPS)

I downloaded the ISO file (xubuntu-11.04-desktop-i386.iso) via torrents and burnt it on a DVD. When I put it in my laptop and booted the computer, I got the option of 'Trying Xubuntu without installation' and 'Install Xubuntu'.

Playing around a bit and liking what I saw, I decided to install it. I was following a manual which showed me step by step installation. However the place where I was suppose to get 3 option regarding installation - 

1. Install Xubuntu alongside Windows 7
2. Replace Windows 7 and install Xubuntu
3. Something else

I only got the 2. and 3. option. As was not able to figure out why was this happening. So just to be safe I downloaded Xubuntu 10.04, but the same problem persisted.

Thinking it was a Xubuntu problem, I even tried the same with Ubuntu 11.10, but no luck.

I decide to try for 3. option (though in the manual I was warned that it is better to let an advance user go for this). I was not seeing partitions the way I put it in Windows. So I backed out of this way.

I am not sure what to do - I just want Xubuntu along Windows 7. Can someone help me?

---

### Post by Hakunka-Matata on 2011-10-25
Hello, Welcome.

Please boot to the ubuntu liveCD, use the "Try without installing" option.  Once ubuntu has booted and you have a usable system, open a Terminal and run this code: ```
sudo fdisk -l
```Post the output so we can see how your HDD is partitioned at present.  You will need an empty Ext.4 partition available to install Ubuntu into.

---

### Post by Mark Phelps on 2011-10-25
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by murthy on 2011-10-28
I am also facing the same problem, while trying to install from Live USB.  I have 2 HDs (1TB and GB), with win 7  installed in HDD1.  Xubuntu does not recognise the partitions on HDD1, It has only 2 primary partitions and 3 extended partitions and intend to install xubuntu to one of the extended partitions.  Xubuntu only shows the partitions on HDD2.  fdisk -l gives the following output:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b8372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   419637247   209715200    7  HPFS/NTFS/exFAT
/dev/sda3       419637248  1953516911   766939832    5  Extended
/dev/sda5       419639296  1258500095   419430400    7  HPFS/NTFS/exFAT
/dev/sda6      1258502144  1782790143   262144000    7  HPFS/NTFS/exFAT
/dev/sda7      1782792192  1953523711    85365760    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000488b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   167766794    83883366    7  HPFS/NTFS/exFAT
/dev/sdb2       167766856   976771071   404502108    5  Extended
/dev/sdb5       167766858   587191814   209712478+   7  HPFS/NTFS/exFAT
/dev/sdb6       587191878   976771071   194789597    7  HPFS/NTFS/exFAT

---

### Post by Hakunka-Matata on 2011-10-28
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b8372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   419637247   209715200    7  HPFS/NTFS/exFAT
/dev/sda3       419637248  1953516911   766939832    5  Extended
/dev/sda5       419639296  1258500095   419430400    7  HPFS/NTFS/exFAT
/dev/sda6      1258502144  1782790143   262144000    7  HPFS/NTFS/exFAT
/dev/sda7      1782792192  1953523711    85365760    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000488b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   167766794    83883366    7  HPFS/NTFS/exFAT
/dev/sdb2       167766856   976771071   404502108    5  Extended
/dev/sdb5       167766858   587191814   209712478+   7  HPFS/NTFS/exFAT
/dev/sdb6       587191878   976771071   194789597    7  HPFS/NTFS/exFAT
```@pri1728: please post the output of following: ```
sudo fdisk -l && sudo sfdisk -luS
```@murthy: your sdb drive has no extra space available in which to install an Ubuntu OS.  sda HDD has a screwed up partition table, but I cannot tell exactly how that happened.  Did you create partitions using Windows Disk Manager?  Can you post a shot of what Windows Disk Manager shows for disk partitioning?  I suspect your sda has been converted (by windows) to dynamic disk, but it's not exactly showing that with fdisk-l, post output of "sfdisk -luS" please.

---

### Post by murthy on 2011-10-28
@Hakunka-Matata: Thanks for the quick reply.  My sda got fixed by using 'fixparts' and it is now seen in gparted.  However my sdb is now shown by windows7 as unformatted and gparted shows some problems in the partition table.  I had not touched sdb in fixparts.  sdb had some contents and I do not know what happened to it.  I will try again with fixparts or gparted.

---

### Post by critin on 2011-10-28
murthy,
<<.*Hakunka-Matata said:*  Did you create partitions using Windows Disk Manager? >>>[I]

and on the post right above your first reply,[/I] <<<Mark Phelps warns: Use only the Win7 Disk Management utility with Windows 7>>

You replied: *<<*  I will try again with fixparts or gparted.>>
Did you understand their advice?  Be careful not to lose your windows os.

---

### Post by murthy on 2011-10-31
Thanks for the warning/advice.  I did understand.  But after trying several times without success, I deleted the extended partition of sda and created logical partitions with gparted using partedmagic 6.7.  Then xubuntu installer recognised the harddisk and also the win7 installation and I had no problem in installing xubuntu to one of the logical partitions of sda.  In my case it appears that the partition done by win7 during its installation was causing problems to xubuntu.

---

