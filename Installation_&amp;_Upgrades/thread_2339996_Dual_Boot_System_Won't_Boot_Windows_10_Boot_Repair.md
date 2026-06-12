---
title: "Dual Boot System Won't Boot Windows 10 Boot Repair NOT Working To Resolve"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by openartist2016 on 2016-10-14
I recently installed Xubuntu on my Windows 10 system.
Now my PC will not boot to Windows 10.Here is the boot report::confused::confused::confused:

[http://paste2.org/9f8VFPLs](http://paste2.org/9f8VFPLs)

Any help would be greatly appreciated.

---

### Post by oldfred on 2016-10-14
You almost never install grub to a partition, just to MBR. And you never, ever install to a NTFS partition.
Windows has essential boot info in the NTFS partition's boot sector or PBR.
You did install grub to sda1, the Windows NTFS partition and that is why Windows cannot boot.
But NTFS does keep a backup and you can usually just restore the backup with testdisk.

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

