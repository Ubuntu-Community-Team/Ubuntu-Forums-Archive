---
title: "Windows not Booting"
date: 2015-09-06
forum: MINT
---

### Post by Aron_Kerenyi on 2015-09-06
Hi,
I'm very new to Linux so this must have been answered before, but I couldn't find it, sorry. I've just installed Linux Mint on my laptop, which has been running Win7 for about a year. One 500 GB hard drive, which originally had a Windows partition and a data partition. Mint installed automatically without formatting any drives, but afterwards I couldn't boot into Win7. After running Boot-Repair, the only thing that changed was that Memtest is now offered as an option. Here is the log:

[http://paste2.org/20WbVwzO](http://paste2.org/20WbVwzO)

Thanks a lot!

---

### Post by oldfred on 2015-09-06
Since Mint and not really an issue that Boot-Repair fixes, moved to your own thread.

```
sda1: _______________________________________________

  
        File system:       vfat
         Boot sector type:  Grub2 (v1.99-2.00)
         Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1 
                            and looks at sector 752481680 of the same hard drive 
                            for core.img. core.img is at this location and looks 
                            for (,msdos6)/boot/grub. No errors found in the Boot 
                            Parameter Block.
         Operating System:  
         Boot files:        /bootmgr /boot/bcd /KERNEL.SYS /COMMAND.COM
```

You installed grub to the PBR or partition boot sector of a NTFS partition. While it says no errors and testdisk may say it is valid, you cannot install grub to a NTFS partitions boot sector. Windows has its own essential boot code there.
NTFS partition do have a backup and normally you can just restore that with testdisk.

       [http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot

It also now says it is FAT formatted. I thought BIOS Windows only booted from NTFS partition. You may need to use Disks to change type to NTFS, but do not reformat. Do not  know if Mint has Disks program? You should back up partition, just in case anyway. If change of type does not work then you may have to delete & recreate as NTFS.
Or
 change sda1 to type 07
sudo sfdisk --change-id /dev/sda 1 07

---

