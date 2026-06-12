---
title: "Windows 7 don't start after dual boot with ubuntu 13.10"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by mahmut999 on 2013-12-22
Hey guys.

I recently installed Ubuntu 13.10 next to a Windows 7 Home Premium  64-bit installation. I only have one 640GB HD in my pc. The HD had three  partitions before the installs. I took some space from the partition  that I use for Windiws7 and created a new partition for the Ubuntu  installation (using the Ubuntu installer). The grub loader displays both  operating systems, but when I boot windows it only displays a black  screen for a second and then reverts to the grub loader. Ubuntu works  fine (has some bugs but works at least).

boot repair report:
[http://paste.ubuntu.com/6617318/](http://paste.ubuntu.com/6617318/)

Note: I also have wubi 12.04 installed in win7

I have something called UEFI in my boot settings. If that has anything to do with it.

Any help with getting my windows to boot again would be appreciated.

---

### Post by oldfred on 2013-12-22
You installed grub to the PBR or partition boot sector of the Windows NTFS partition. Windows has to have its boot code and partition info in all NTFS PBRs (even if not bootable).
Your installs are all BIOS, do do not boot in UEFI mode. 

      ```
 sda2: __________________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 1141020096 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 94 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows 7

```    

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR similar instructions:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

