---
title: "UltraBook boot issues from install on SSD"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by daniela89 on 2013-04-21
I have the exact same problem. Have spend almost 24hours debugging.. I just want to get my windows system back. I cannot reinstall, have too many programs on here.

I have a UX32VD with the onboard 24GB SSD and a 256 m4 SSD primary. I had Windows on my 256 SSD and tried to dual boot by installing ubuntu 12.04 LTS on the 24GB ssd. 
Now i can only boot to ubuntu, windows is not booting. 

here is some info on my system:

I have tried everything from:
manually updating the grub files
running grup-repair
running grub-customizer 
running windows recovery (now I cannot even boot from a windows recover disk)
reinstalling ubuntu 

PLEASE help. I would really appreciate it!




pastebin is not working so i pasted my info below:


```
============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Boot/bootx64.efi /ubuntu/grubx64.efi 
                       /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi /Microsoft/Boot/bootmgfw.efi 
                       /Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 256.1 GB, 256060514304 bytes
256 heads, 63 sectors/track, 31009 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   500,117,503   499,648,512 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       976,895       974,848  83 Linux
/dev/sdb2             978,942    46,903,295    45,924,354   5 Extended
/dev/sdb5           4,884,480    46,903,295    42,018,816  83 Linux
/dev/sdb6             978,944     4,882,431     3,903,488  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 64.0 GB, 63999836160 bytes
255 heads, 63 sectors/track, 7780 cylinders, total 124999680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,128   124,999,679   124,997,552   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FA78-C371                              vfat       
/dev/sda3        9AE09FDFE09FC045                       ntfs       
/dev/sdb1        30fa1445-94a5-4914-9825-4128db37b254   ext4       
/dev/sdb5        231055eb-bd6f-4533-a642-6e491aea3f1f   ext4       
/dev/sdb6        829a2740-88f4-478f-8aed-6083fd5a0382   swap       
/dev/sdd1        60BEE05CBEE02BEA                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


============================= sdb1/grub/grub.cfg: ==============================
```

---

### Post by oldfred on 2013-04-21
Moved to your own thread was here:
[http://ubuntuforums.org/showthread.php?t=2136920](http://ubuntuforums.org/showthread.php?t=2136920)

Please do not highjack another's thread. Boot issues are almost always unique and your issue is a lot different, so it will not help OP.

It looks like you originally installed in BIOS mode not UEFI and then your 24GB SSD became MBR(msdos) not gpt.
I do not think you can boot Ubuntu in a MBR drive even though Boot-Repair has added an efi boot entry to the efi partition on sda.

Manually partition sdb and include an efi partition at beginning of that drive. It may not be used, but best to have it on every gpt drive. Then reinstall in UEFI mode. A few systems will not let you install in UEFI mode, if your is one you can reinstall as Ubuntu will boot in BIOS mode from gpt partitioned drives, but then the conversion by Boot-Repair should work. You may have to undo the renaming that Boot-Repair did to the efi partition first and get Windows booting again.

See last couple of lines on undo:
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

