---
title: "Dual boot Windows 7 doesn't start after lubuntu installation"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by cristoforo2 on 2014-09-28
Hi all,

I'm trying to set up a dualbooting windows 7 and lubuntu 14.04 machine. I've installed Windows first, and then Lubuntu.
When the machine starts grub find out the windows 7 os but it's impossible start it.
I've tried with super grub boot loader and with boot-repair. At this link you can find the log : [http://paste.ubuntu.com/8446634/](http://paste.ubuntu.com/8446634/)

Thanks a lot for help

---

### Post by fantab on 2014-09-28
Windows filesystem on NTFS partitions seems damaged.
Since Windows is not bootable, and if you have either windows Repair Disc or Install Disc then you follow this:[ http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html]("http://www.sevenforums.com/tutorials/433-disk-check.html")
and fix windows boot. This will restore your Windows but you will lose grub.
Run [Chkdsk]("http://www.sevenforums.com/tutorials/433-disk-check.html") on all the Windows NTFS partitions... reboot Win atleast twice.
Reinstall Ubuntu Grub using boot-repair tool.

There also seems to an issue with your Extended partition or /dev/sda3, which can be fixed with [fixparts]("http://www.rodsbooks.com/fixparts/") easily.

---

### Post by oldfred on 2014-09-28
You installed grub to the PBR or partition boot sector of sda1 which is the NTFS Boot partition. NTFS has to have Windows data in the PBR.

```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 295107200 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
```

NTFS does save a backup which if still ok, you can easily restore using testdisk. Testdisk may say the grub is valid as it probably is installed correctly to the PBR, but with NTFS it cannot be there if you want Windows to work.

 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If backup is invalid, you have to use testdisk to add a XP type NTFS signtuare and then may be able to run chkdsk from a Windows repair CD or flash drive. Or you have to run bootsect.exe to replace partition boot sector, also from a Windows repair disk. I think the fixBoot with Windows may just copy the backup, but if PBR not seen as NTFS which with grub it will not, then you cannot even run chkdsk.

---

### Post by cristoforo2 on 2014-09-28
Hi all,

thanks for support. I'm trying to use TestDisk but when I select the NTFS partition the result is:

Boot sector
Status : OK

Backup boot sector
Status : OK

Sectors are identical.

And  I've only 5 actions:
[Quit] 
[List] [Rebuild BS] [Repair MFT] [Dump]

If I select Rebuild BS and then list I can choose only among linux directories.

Thanks a lot

---

### Post by oldfred on 2014-09-28
You have to run Rebuild BS (bootsector) just to even get Windows to recognize that it is a NTFS partition.
Then you should be able to run chkdsk from a Windows repair CD or flash drive.

The testdisk creates a default NTFS BS but I believe it still is XP based and if trying to boot directly from that it may try to boot with ntldr. After chkdsk from Windows newer version, it will update PBR to use bootmgr to boot and then should be ok.

Or use bootsect.exe from your Windows repair disk to totally write a new boot sector. Your Windows repair disk needs to be the same 32 bit or 64 bit version as your install.

---

