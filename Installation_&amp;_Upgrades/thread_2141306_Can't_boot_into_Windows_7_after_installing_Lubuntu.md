---
title: "Can't boot into Windows 7 after installing Lubuntu 13.04"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by micecream on 2013-05-02
Hi,

So I shrinked my only partition with Windows, and installed Lubuntu in dual-boot. Now, when I select Windows in the grub menu, it just redirects me to that menu again. I can boot into Lubuntu though. Here's the boot-repair report: [http://paste.ubuntu.com/5625718/](http://paste.ubuntu.com/5625718/). 

How do I fix this?

Thanks.

---

### Post by oldfred on 2013-05-02
NTFS has to have an NTFS PBR or partition boot sector. You installed grub to the PBR. NTFS does keep a backup and you can use test disk to easily restore backup if backup is valid.

```
 sda1: _________________________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 84020640 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 94 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


```

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by micecream on 2013-05-02
oldfred, thank you very much! The first option helped me, and I can now boot into both Windows and Lubuntu. I would be more grateful if you point at possible wrong actions leading to this problem, as it's not my first time of installing a Linux distro alongside with Windows, but first time I run into this problem.

---

### Post by oldfred on 2013-05-02
I always use manual install and choose the drive sda, sdb etc on where to install the grub2 boot loader. You never (almost never) install to a partition and never to a NTFS partition.
 
I think since 10.10 we have filed bug reports that grub should never install to a NTFS PBR, and either installer says it grub or grub says its the installer or one fixes it and later it regresses.

---

