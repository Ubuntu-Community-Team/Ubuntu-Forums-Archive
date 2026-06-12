---
title: "Windows 7 won't startup after ubuntu installation&#8207;"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by alexandre10 on 2014-05-11
[http://paste.ubuntu.com/7450411/](http://paste.ubuntu.com/7450411/)
I've tried boot-repair with the recomended settings but it is still not working.
boot-repair log follows up.
I couldn't solve the problem by myself. I was wondering if you can help me.
Windows 7 wont startup after ubuntu installation.

Thank you,
Alexandre

---

### Post by kc1di on 2014-05-12
Is this a uefi /secureboot machine?

---

### Post by GeorgeLSpencer on 2014-05-12
Did you install Ubuntu on a separate partition or disk? If you installed it onto the Windows partition then you have probably overwritten Windows 7. If you installed it on a separate partition or disk then for some reason grub is not seeing the Windows partition. You could try "Grub Customiser" as this searches for the extra OS's and as well as adding them to GRUB menu. Grub will find Windows 7, if it is located on a separate partition or disk. I have each OS on a separate disk and both Grub and Burg find them without a problem.

---

### Post by LastDino on 2014-05-12
Before installing grub customizer update grub. Usually that does the trick enough.

---

### Post by oldfred on 2014-05-12
You cannot install grub2's boot loader to a NTFS partition's PBR or partition boot sector. Windows has essential boot code in the PBR.

```
 sda2: ____________________________
   File system:[COLOR=#ff0000]       ntfs[/COLOR]
    Boot sector type:  [COLOR=#ff0000]Grub2[/COLOR] (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 955648024 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.


```

Use testdisk to restore from backup PBR.

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

Then to add Windows to grub menu run this after rebooting into your install.
sudo update-grub

---

### Post by alexandre10 on 2014-05-17
i belive yes

---

### Post by alexandre10 on 2014-05-17
> **oldfred said:**
> You cannot install grub2's boot loader to a NTFS partition's PBR or partition boot sector. Windows has essential boot code in the PBR.

```
 sda2: ____________________________
   File system:[COLOR=#ff0000]       ntfs[/COLOR]
    Boot sector type:  [COLOR=#ff0000]Grub2[/COLOR] (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 955648024 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.


```

Use testdisk to restore from backup PBR.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

sudo update-grub


SOLVED!
Thank you so much.
Followed tutorial for testdisk.

---

