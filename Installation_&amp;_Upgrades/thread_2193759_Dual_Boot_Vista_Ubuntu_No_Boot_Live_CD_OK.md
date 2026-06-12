---
title: "Dual Boot Vista Ubuntu No Boot Live CD OK"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by sredmail on 2013-12-14
Hi,

I have a Ubuntu install.

No access to Vista Repair Disks

This is a old Laptop that I want to donate working.

It won't boot (used too) after Ubuntu update.

Has Dual Vista Ubuntu Boot config.

[http://paste.ubuntu.com/6574569/](http://paste.ubuntu.com/6574569/)

---

### Post by bashiergui on 2013-12-14
If you want to donate it why would you try to repair Ubuntu? I would remove the broken Ubuntu installation and put Vista on the whole drive. Or do a fresh install of Ubuntu over the whole drive.

---

### Post by sredmail on 2013-12-15
> **bashiergui said:**
> If you want to donate it why would you try to repair Ubuntu? I would remove the broken Ubuntu installation and put Vista on the whole drive. Or do a fresh install of Ubuntu over the whole drive.

This is being donated to Friends who are unable to afford paying for a new or used laptop in another Country in Central America.

1. They have kids 7 & 9 years old that play kids (same as at their friends house) games specific to windows so it still needs to be Dual Boot.

2. The Parents will use Linux Open Office for their needs, one of them is taking course at the local College.

Thanks for your help.

---

### Post by oldfred on 2013-12-15
Script is showing grub installed to the PBR - partition boot sector of your recovery partition. You almost never install grub to a partition and never to a NTFS partition

```
 sda1: _________________________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 410707426 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.


```
This should fix recovery. It looks like a vendor recovery not a Windows recovery. That is it restores system. But the Install of Ubuntu may then be erased.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

But script is not mounting your sda2. Often that is either hibernation or it needs chkdsk. You have to run chkdsk from a Windows repairCD or flash drive or if f8 gets you to a Windows. Often grub boot of Windows is too fast for f8, some do try many times at the same instant of hitting key to boot Windows in grub menu. But you do not currently have an entry for Windows in sda2 as partition cannot be mounted to see the install.

It looks like you told Boot-Repair to install grub to sdb, or the flash drive. That then will only work to boot install in your hard drive on sda. Flash drive would have to be created again as it does not use grub to boot, but syslinux, a Windows type boot loader.

---

