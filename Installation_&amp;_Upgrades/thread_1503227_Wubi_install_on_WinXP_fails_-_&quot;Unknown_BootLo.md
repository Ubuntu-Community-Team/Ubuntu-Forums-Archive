---
title: "Wubi install on WinXP fails - &quot;Unknown BootLoader  on sda1/Wubi&quot;"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by jnorville on 2010-06-06
Installing Wubi 10-04 on a relatively-fresh XP install on an older Dell laptop (630).

All appeared to go well -- but on reboot I didn't get a prompt from the Windows Boot Loader with a choice of OSs as I think I was expecting.

Other similar threads generally request the boot_info_script55.sh output -- downloaded and ran it, appears to fail in the boot info section.  I am able to boot into a livedisk session.

So, here's the output of the boot_info_script (and thanks in advance for your tips):
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1049 MB, 1049624576 bytes
29 heads, 28 sectors/track, 2524 cylinders, total 2050048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  64     2,050,047     2,049,984   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        34A0046FA0043A3E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6464-2448                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/6464-2448         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200



```

---

### Post by bcbc on 2010-06-07
well the timeout in your windows menu is 0 seconds, so that's why you don't see a menu. But, the wubi install is blank or at least it appears to contains zeroes, the file system is unknown and non-mountable. So, I recommend uninstalling and reinstalling.

Wubi installs work like this: you see the windows 'installation' which involves downloading the CD image (if necessary), installing grub bootloader for dos, and creating virtual disks. Then when you reboot (and select ubuntu) it does the ubuntu installation on the virtual disks. So if you didn't see this part (and I'm guessing you didn't) then you need to try again.

Hope that helps!

---

