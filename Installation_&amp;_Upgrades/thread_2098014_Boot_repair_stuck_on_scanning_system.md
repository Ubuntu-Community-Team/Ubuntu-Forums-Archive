---
title: "Boot repair stuck on scanning system"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by nlinggod on 2012-12-25
I recently tried to dual boot Ubuntu onto my PC alongside Win7.

After the installation I could no longer access Win7. It would just go back to the grub screen whenever I clicked on the Windows option. After a bit of searching I thought I'd try Boot repair.

I've installed it, updated it and tried to run it but it just says "Scanning. This may take a few minutes".

The progress bar moves back and forth so it looks like it is doing something but never gets beyond this point. So far I've left it as long as an hour with no change.

Anyone have any ideas?

---

### Post by nlinggod on 2012-12-25
Alright, Boot repair seems to run now. I've no idea how or why it started but anyway.

I set it to repair and seemingly did so but I still had the same problem.

That of being sent back to the screen where I choose which OS to start up when ever I choose windows. The Ubuntu side seems to work fine though.

AFter a bit more reading I tried running Boot Repair again, this ticking the repair MBR option too. Still no change.

The boot info summary is here:

[http://paste.ubuntu.com/1466134/plain/](http://paste.ubuntu.com/1466134/plain/)

Anyone have an idea of what's going on and what I can do?

---

### Post by oldfred on 2012-12-25
Usually scanning like that is that it cannot open a partition. And LInux does not open NTFS partitions that need chkdsk.

But your issue is that you installed grub to sda1 the NTFS partition, not sda the hard drive's MBR which is used to boot.

You are now booting Ubuntu with the Windows boot loader. It finds the partition with the boot flag and jumps to that partition to boot which should be a Windows partition. But since you installed grub to the Windows partition you can boot Ubuntu but will never be able to boot Windows. Windows has to have a NTFS boot signature in the PBR - partition boot sector. That tells Windows which boot loader to use XP or Vista/7 and partition size.

NTFS partitions do have a backup and you can use testdisk to restore from backup. But install grub2's boot loader to the MBR first.

Boot into Ubuntu and run this:
       sudo grub-install /dev/sda

Then download testdisk and run it. Details in either of these:
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

---

