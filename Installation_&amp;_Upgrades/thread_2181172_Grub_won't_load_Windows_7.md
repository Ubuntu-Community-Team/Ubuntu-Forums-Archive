---
title: "Grub won't load Windows 7"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by Joel_Bijapurkar on 2013-10-16
Hi,
I have installed Ubuntu 12.04 LTS on my laptop. During installation I selected the "some-thing else option" as I already had Windows 7 installed.  In the "device for boot-loader" dropdown menu I chose "Windows 7 loader on sda1". But now Windows is not starting up. When I switch on my laptop, grub does have an option for Windows on /dev/sda1 but on selecting that option the screen goes black for a few seconds and returns to grub. I tried using BootRepair and got the following report:   _**[http://paste.ubuntu.com/6246530/](http://paste.ubuntu.com/6246530/)**_ . I also tried recovering Windows with the recovery option present in the backup discs. The recovery was completed and a fresh copy of Windows was installed, but again grub failed to start WIndows. So how can I load Windows OS again?
Thank You.

---

### Post by oldfred on 2013-10-16
Welcome to the forums.
I thought with all the bug reports we have filed on your issue they would eventually fix it. The installer should never let you install grub2's boot loader to a Windows NTFS partition. Windows has to have its own boot code in the NTFS partition. Grub2's boot loader normally should be in MBR or only extremely rarely installed to the PBR or partition boot sector of the Ubuntu partition or boot partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

Or:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

