---
title: "Just installed 12.04.1 alongside Windows 8, ubuntu wont boot."
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by Phife420 on 2012-09-11
I just installed Ubuntu 12.04.1, I choose the alongside windows 8 option, I choose to divide a partion or something like that, my D drive, windows 8 is on my C drive, anyways fast forward, Im asked to restart, I continue, when it boots up it boots into windows 8 as if nothing has happen however I lost the 178ish partition I divided earlier, so I know its somewhere, just not able to view from windows 8 though.

I just went through the boot repair, and I havent tested if it worked out yet, if it does im gonna remove this thread anyways just leaving it here since if it doesnt after im rebooting in a few minutes ill be going to sleep and then I wont have to return to make this thread.

[http://paste.ubuntu.com/1199490/](http://paste.ubuntu.com/1199490/) There is the log provided by it.

Anyways much love.

EDIT: Nevermind this was fixed by the boot repair, sorry for making this unnecessary thread.

---

### Post by oldfred on 2012-09-11
Glad Boot-Repair Worked. It looks like you may have installed grub to the partition not the MBR. 

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Your sda5 partition is a NTFS partition. It has to have NTFS in the partition boot sector not grub. You can use testdisk (and other tools) to restore the backup partition boot sector.

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

### Post by YannBuntu on 2012-09-11
> **Phife420 said:**
> this was fixed by the boot repair

Good job :)

For our information (in order to understand why GRUB is in sda5's bootsector):
which option did you choose in [this installation menu]("http://pix.toile-libre.org/upload/original/1312973605.png")?
If you choose "Something else", did you change the "Device for bootloader installation" (at the bottom of [this screen]("http://doc.ubuntu-fr.org/_media/installation_graphique/partitionner_manuellement_avec_installateur_ubuntu_3.png?cache=")) ?

---

