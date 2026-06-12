---
title: "Unable to boot into Windows 7 on dual boot"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by ramesh-gopalakrishna on 2014-02-09
I had Ubuntu 13.10 and Window 7 installed as dual boot. I added another linux installation Linux-Mint to the mix. I am able to boot into both of the linux partitions, but not able to boot to Windows 7.

Here is the output of boot-repair: [http://paste.ubuntu.com/6904136/](http://paste.ubuntu.com/6904136/)

---

### Post by oldfred on 2014-02-09
You cannot install grub to the PBR or partition boot sector of a NTFS partition.

```
 sda1: ____________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 617664736 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 94 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


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

You do have Windows in a logical partition. Real requirement is that it must boot from a primary which you have, but often better to keep all Windows on primary partitions. You may need chkdsk on sda8, as it shows some discrepancies in size. The Windows PBR must have same start & size info as partition table and Windows boot code to work correctly.
Show Vista but applies to all Windows in MBR boot mode.
       Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

