---
title: "Dual-boot Ubuntu 14.04 and Windows 7. Windows will not boot."
date: 2015-03-08
forum: Installation &amp; Upgrades
---

### Post by bbrydsoe on 2015-03-08
Quick background: 

I have a HP 350 laptop with Windows 7, and decided to dual-boot it with Ubuntu 14.04. Haven't done that since Windows Vista, and turns out there were problems ;)

The laptop had four primary partitions already set up. I converted C: to logical, since boot lived on a different partition. This went well, and Windows would still boot. I shrank the partition so I got about 200 GB to install Linux on. Windows still booted happily. 

I installed Linux from USB. The installer did not detect Windows, but would happily install on the unallocated space I had made earlier. Installation finished and Ubuntu booted. No problem. 

Problem: 

I had no entry for Windows 7. I took a look at /boot/grub/grub.cfg and there was no entry there. Running grub-mkconfig found Windows and created a new grub.cfg. 
I now had an entry for Windows 7 in grub when I rebooted, but choosing that only resulted in the computer briefly blinking a black screen and then going back to grub. 
I ran Windows repair disc and it said all was well :(

I also ran boot-repair, but it did not fix the problem. This link: [http://paste.ubuntu.com/10559617/](http://paste.ubuntu.com/10559617/)

I am assuming the problem is in the boot-loader, but I have no idea what to do. Help?

-Birgitte

---

### Post by oldfred on 2015-03-08
It looks like you installed grub to the partition boot sector (PBR) or sda1 originally. You normally only install grub to the drive's boot sector or MBR or the very first sector of the hard drive - sda. And you never install grub to a NTFS partition's boot sector as it has Windows boot info.

```
 sda1: _______________________________________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1 
                       and looks at sector 562296512 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


```

But NTFS partitions keep a backup of the PBR, so you can use testdisk to restore the PBR, if only overwritten once.

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Most users change or delete the HP tools partition as it is smaller and can be downloaded from HP.

---

### Post by bbrydsoe on 2015-03-08
That fixed the problem! 

Thank you!

---

