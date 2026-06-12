---
title: "Wubi-Install: After Kernel-Update(20Dec) grub.cfg is gone"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by babdare on 2010-12-20
Hello!:)
 
i have a Winxp and Ubuntu 10.10 system(wubi-install, update from 10.04 to 10.10).
I have fixed the update problem 10.04 to 10.10 with the modified wubildr.
Today there was a kernel update  from 2.6.32 to 2.6.35 (???) and after the restart i can boot only xp.
If i choose Ubuntu, there is a black screen and the computer restart. the ubuntu\disks\boot\grub folder is empty!?!

Here is my log:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sda2          71,682,030   312,560,639   240,878,610   f W95 Ext d (LBA)
/dev/sda5          71,682,093   312,560,639   240,878,547   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3b9cec62-504f-464b-be56-c4e87a606129   ext4                                     
/dev/sda1        64C4AEEEC4AEC222                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2E64A09964A064F5                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/2E64A09964A064F5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINXP
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINXP="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr="Ubuntu" 

```

---

### Post by drs305 on 2010-12-20
If the only problem is that grub2 was corrupted or removed, you can try to restore it by booting from a Maverick LiveCD, then chrooting into your Wubi install and reinstalling grub-pc.

The instructions are in the following link. Use the 'Chroot' section of the guide. Make sure you follow the Wubi mounting instructions. It probably isn't necessary to run the purge command but it would probably be best to ensure you get uncorrupted files. In the "apt-get purge" command you do not need to include "grub", just "grub-pc" and "grub-common".
[http://ubuntuforums.org/showthread.php?t=1581099]("http://http://ubuntuforums.org/showthread.php?t=1581099")

**Added:** You may need to repair the grub.cfg file in the same way you did after the update. You can also refer to this thread for more about solving Wubi problems:
[Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by babdare on 2010-12-20
thx, i give it a try, great tut by the way...

---

