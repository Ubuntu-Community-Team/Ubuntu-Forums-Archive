---
title: "How to solve multi-boot problem to boot windows 7 after installing ubuntu"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by Rahul_Choudhary on 2015-11-03
[FONT=arial, sans-serif]Hello,[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I am trying to boot my windows 7 after installing Ubuntu 14.04, but its redirecting to the same GNU GRUB page.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]sudo add-apt-repository ppa:yannubuntu/boot-repair
[FONT=inherit][/FONT]sudo apt-get update
[FONT=inherit][/FONT]sudo apt-get install -y boot-repair && boot-repair[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]When I run above command in terminal I got URL: [http://paste.ubuntu.com/13098939](http://paste.ubuntu.com/13098939)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Please help me how I will solve this problems.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Regards,[/FONT]
[FONT=arial]Rahul Choudhary[/FONT]

---

### Post by Bucky Ball on 2015-11-03
*Thread moved to **Installation & Upgrades**.*

The ***Resolution Centre*** is for issues with the forum itself, not for support requests regarding Ubuntu. :)

Open a terminal and try running this:

```
sudo update-grub
```

Reboot. Is Windows now on the list and bootable? Did you run Boot Repair's recommended repair option?

* But, just noticed these anomalies from you output:

```
Windows not detected by os-prober on sda2.
Warning: extended partition does not start at a cylinder boundary.
```

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   209369448   104581300+   7  HPFS/NTFS/exFAT
/dev/sda3       209369576   315281246    52955835+   7  HPFS/NTFS/exFAT
/dev/sda4       315281374   976771071   330744849    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       315281376   692768735   188743680    7  HPFS/NTFS/exFAT
/dev/sda6       692772864   941580063   124403600    7  HPFS/NTFS/exFAT
/dev/sda7       941580288   968638463    13529088   83  Linux
/dev/sda8       968640512   976771071     4065280   82  Linux swap / Solaris
```

```
sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:
```

There appears to be an issue starting with sda4, your extended partition.

---

### Post by oldfred on 2015-11-04
Never install grub to a partitions boot sector or PBR.

```
sda1: ______________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1 
                       and looks at sector 955602168 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

```

NTFS does keep a backup of the PBR and you can use testdisk to restore from the backup. Testdisk may say PBR is valid as grub can be in a PBR, but never in a NTFS PBR. Windows has its own essential boot info in the NTFS PBR.

       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

