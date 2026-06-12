---
title: "Replaced Windows XP (hd0,0) grub with  a ubuntu one. How to rebuild it ?"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2008-11-15
Because I was tired, I wanted to update my (hd0) grub and accidentally wrote (hd0,0) instead. So now I cannot boot to my Windows XP who was using that (hd0,0) as its grub.

How do I rebuild/restore it ?

---

### Post by Clogger on 2008-11-15
> **Browser_ice said:**
> Because I was tired, I wanted to update my (hd0) grub and accidentally wrote (hd0,0) instead. So now I cannot boot to my Windows XP who was using that (hd0,0) as its grub.

How do I rebuild/restore it ?


Try Super Grub Disk -

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Herman on 2008-11-15
There are a few ways I know of to fix that, depending mainly on what resources you have available.

One way that's easy is if you have your Windows XP 'Installation Disc', (as opposed to a 'Recovery CD'. You should be able to just put in your Windows XP install CD, and boot into the [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the famous 'FIXBOOT' command.

Another way if you have Windows XP with the FAT32 file system, is to fix it from Linux, (Ubuntu).
Boot Ubuntu and read this link, [When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup").
If you followed the steps in that example you should have been easily ablt to restore your Windows XP boot sector from it's backup if you have your Windows XP installed in the FAT32 file system.

If you have Windows with the NTFS file system, here is the link for you, [Restore an NTFS boot sector with it's backup]("http://users.bigpond.net.au/hermanzone/p10.htm#Restore_an_NTFS_boot_sector_with_its"). Once again, you can fix it from Ubuntu but this time you need to install TestDisk first. The NTFS file system stored it's backup boot sector in the last sector of the partition.

There are more ways to fix it too, [MbrFix.exe]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe") will probably work also, I'm not sure, and maybe Super Grub Disk.
Clogger suggested Super Grub Disk, I'm sure older versions of Super Grub Disk had an equivalent for the FIXBOOT command, maybe they still do, and maybe even an  improved program for that, I'm not up to date on that info at the moment.

---

### Post by meierfra. on 2008-11-15
Edit: Hadn't seen Herman post, then I posted this. This is the same as Herman's "Restore an NTFS boot sector with it's backup."   

You can recover the Windows boot sector with testdisk:

```

sudo apt-get install testdisk

sudo testdisk
```

After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the XP partition, choose "boot", then choose "Backup BS", and have testdisk write the backup boot sector to the partition boot sector.

---

### Post by cdtech on 2008-11-15
To fix the boot sector of a NTFS partition, you could use the program "testdisk".
```
sudo apt-get install testdisk
```
Start "testdisk"
```
sudo testdisk
```
Choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the NTFS partition you want to fix, choose "boot", then choose "Backup BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". 

That should fix the boot sector of that NTFS partition.

Hope this helps ya....

---

### Post by cdtech on 2008-11-15
lol

---

