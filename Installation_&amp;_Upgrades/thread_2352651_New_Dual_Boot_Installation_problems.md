---
title: "New Dual Boot Installation problems"
date: 2017-02-14
forum: Installation &amp; Upgrades
---

### Post by vanilla8 on 2017-02-14
Installed Ubuntu alongside Windows 10 on my Sony Vaio Laptop, from a bootable USB, but something has gone wrong, as I now cannot boot into Ubuntu without the below error:

```
Kernel panic - not syncing: No working init found. Try passing init=option to kernel
```

I cannot boot into Windows 10 either.
I installed the boot manager on the same partition as the windows boot one, but installed Ubuntu on a different partition.

I have booting back into Live USB and created boot info script here [http://pastebin.com/np6LMmc4](http://pastebin.com/np6LMmc4)

Can anyone help!

---

### Post by oldfred on 2017-02-14
You broke Windows by installing grub to the Windows boot partition's PBR or BS partition boot sector.
Windows boots, from BIOS to MBR to PBR. It has to have more Windows code in PBR and partition info. So having grub in the PBR prevents Windows from working.
And since grub is in partition normal Windows repairs will not work as Windows does not even see it as a NTFS partition.

Fortunately NTFS keeps a backup and that can be restored using testdisk. Teskdisk may say PBR/BS is valid as having grub in a PBR can be valid. So if backup is valid, just restore it. If backup not valid run the commands to create a new BS, but then you have to run chkdsk from a Windows repair disk to finish the fixes.

       Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

You normally only install grub to MBR of a drive like sda, almost never to a PBR like sda1, sda2 etc. And never to PBR/BS of NTFS partitions.

After fixing Windows, run Boot-Repair and reinstall grub to MBR of sda.

---

### Post by vanilla8 on 2017-02-14
Thanks! All fixed! :)

---

### Post by oldfred on 2017-02-14
You can change to Solved.

---

