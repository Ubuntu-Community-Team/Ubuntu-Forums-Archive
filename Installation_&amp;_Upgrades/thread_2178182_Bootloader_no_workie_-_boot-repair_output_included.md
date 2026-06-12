---
title: "Bootloader no workie - boot-repair output included"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by biffta on 2013-10-02
I was hoping a kind person might be able to take a look at the following output from [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") and tell me why my Windows 7 partition fails to boot

[http://paste.ubuntu.com/6183235/](http://paste.ubuntu.com/6183235/)

Many Thanks!

---

### Post by oldfred on 2013-10-02
You installed grub to the Windows PBR - partition boot sector. Windows has essential boot code in the PBR.

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

### Post by biffta on 2013-10-02
> If the sixth screen did not have a "BackupBS" tab, it usually means that the original and backup boot sector are identical, and you are probably suffering from a different problem.

Dam. Are there any other suggestions? I don't have a Windows CD to repair with.

---

### Post by oldfred on 2013-10-02
If you still have grub in PBR, even a Windows repairCD will not fix it as it will not see it as a Windows NTFS partition. If backup not valid use the rebuild BS to create a new NTFS Boot Sector.
At the very least you have to create the NTFS PBR with testdisk. But that is a XP type PBR, and you will need a Windows repairCD or flash drive to convert from XP type (ntldr) to Vista/7/8 type that uses bootmgr. PBR calls out boot file to use based on install. 
Chkdsk should fix it and some third partition Windows repair tools may run chkdsk. You cannot run chkdsk from Linux.

       Third party chkdsk tools
Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
May be able to run chkdsk from Hiren's boot CD. (mini xp.)
Hiren's Boot CD, and do a chkdsk on the XP

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

### Post by RichardET on 2013-10-02
I like to keep everything simple - buy the Windows Restore disk and start over.

---

