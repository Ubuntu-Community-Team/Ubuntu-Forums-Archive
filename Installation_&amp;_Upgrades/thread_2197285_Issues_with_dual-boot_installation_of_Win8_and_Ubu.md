---
title: "Issues with dual-boot installation of Win8 and Ubuntu Studio"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by talondrew on 2014-01-03
Good Evening,

Got new laptop and I'm trying to dual-boot Win8 and Ubuntu Studio. The install went well, but I can't get either OS to load correctly on bootup. I'm having no issues loading into a live-USB version of Ubu Studio. 

When I boot I end up in GRUB and a command prompt. I rebooted into the live-USB and installed / ran boot-repair. Tried it a few times. It says it  has repaired the bootup and fixed the issue, but whenever I boot I end up in GRUB at the terminal-esque interface. 

I have the copy of the report from boot-repair. Just looking for some advice on why I'm unable to have GRUB give me the menu where I choose which OS to load - and why I can't get either OS to load directly.

---

### Post by talondrew on 2014-01-03
Here's the start of that boot-repair report: (haven't posted the whole thing because I don't know if it should be attached, or pasted in completely in the forums?)

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntustudio/MokManager.efi 
                       /EFI/ubuntustudio/grubx64.efi 
                       /EFI/ubuntustudio/shimx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntustudio/shimx64.efi 
                       /EFI/Microsoft/Boot/LrsBootmgr.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..............0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:  Syslinux looks at sector 5130312 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment (Windows)
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     4,630,527     2,048,000 -
/dev/sda4       4,630,528     4,892,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       4,892,672   952,592,383   947,699,712 Data partition (Windows/Linux)
/dev/sda6   1,875,011,584 1,927,440,383    52,428,800 Data partition (Windows/Linux)
/dev/sda7   1,927,440,384 1,953,523,711    26,083,328 Windows Recovery Environment (Windows)
/dev/sda8     952,592,384 1,065,873,407   113,281,024 Data partition (Linux)
/dev/sda9   1,065,873,408 1,097,123,839    31,250,432 Swap partition (Linux)
/dev/sda10  1,097,123,840 1,875,011,583   777,887,744 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7340 MB, 7340032000 bytes
2 heads, 63 sectors/track, 113777 cylinders, total 14336000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64    14,335,999    14,335,936   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F2260B3B260B0079                       ntfs       WINRE_DRV
/dev/sda10       214ca08b-f7b2-4306-8319-6bbb20e0d843   ext4       
/dev/sda2        CA0D-87E5                              vfat       SYSTEM_DRV
/dev/sda3        1C0D-D68F                              vfat       LRS_ESP
/dev/sda5        EE6E11AE6E117097                       ntfs       Windows8_OS
/dev/sda6        D8881A5E881A3B86                       ntfs       LENOVO
/dev/sda7        845214E75214E02A                       ntfs       PBR_DRV
/dev/sda8        0c244dac-28d3-407a-a9ff-1b54534cb4a4   ext4       
/dev/sda9        68212ce2-03b4-4ac2-8473-a4e5af904713   swap       
/dev/sdb1        5091-1293                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

---

### Post by talondrew on 2014-01-03
I have the entire log from boot-repair if that would be helpful to anyone....

---

### Post by talondrew on 2014-01-04
Still reading more about this online and looking for Lenovo specific support - I understand that they have a different setup that may cause extra issues when trying to load the OS and create a dual-boot setup. Not sure if this is in the right area of the forums, or if I can provide any more information that would be helpful.

---

