---
title: "Ubuntu does not boot after installation (Win 7 already installed as a primary system)"
date: 2014-04-09
forum: Installation &amp; Upgrades
---

### Post by michael137 on 2014-04-09
My laptop is Asus k52jc with a Windows 7.I installed it as second system, yet after installation ubuntu 12.04 has not been detected and simply win 7 starts up.
I had an issue during the installation about GRUB, but I don't remember it correctly. I read few topics and run this script [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) which gave me this answer:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS
    Boot files:        /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    40,965,749    40,965,687  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     40,965,752   197,250,679   156,284,928   7 NTFS / exFAT / HPFS
/dev/sda3         197,253,118   625,141,759   427,888,642   f W95 Extended (LBA)
/dev/sda5         197,253,120   481,779,711   284,526,592   7 NTFS / exFAT / HPFS
/dev/sda6         481,781,760   553,869,163    72,087,404   7 NTFS / exFAT / HPFS
/dev/sda7         553,869,312   619,151,359    65,282,048  83 Linux
/dev/sda8         619,153,408   625,141,759     5,988,352  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mmcblk0p1   3C17-14B8                              exfat      
/dev/sda1        3E5F-3A2B                              vfat       RECOVERY
/dev/sda2        10508167508153FE                       ntfs       OS
/dev/sda5        92BC83DBBC83B7ED                       ntfs       Data
/dev/sda6        1E18F05F18F036FD                       ntfs       Linuch n stuff
/dev/sda7        25527b5a-fb52-4ee1-8e7d-0ac565f426be   ext4       
/dev/sda8        88ee4ff1-2cc3-4b1a-a40d-22ad2f8e5f25   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04.4 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=25527b5a-fb52-4ee1-8e7d-0ac565f426be /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=88ee4ff1-2cc3-4b1a-a40d-22ad2f8e5f25 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-3.11.0-15-generic              2
               =                boot/vmlinuz-3.11.0-15-generic                 1
               =                boot/vmlinuz-3.11.0-15-generic.efi.signed      1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  40 5f 57 56 3f 24 43 68  54 72 61 69 74 73 43 52  |@_WV?$ChTraitsCR|
00000010  54 40 5f 57 40 41 54 4c  40 40 40 40 40 41 54 4c  |T@_W@ATL@@@@@ATL|
00000020  40 40 51 41 45 40 50 42  5f 57 40 5a 24 30 00 5f  |@@QAE@PB_W@Z$0._|
00000030  5f 65 68 68 61 6e 64 6c  65 72 24 3f 3f 48 41 54  |_ehhandler$??HAT|
00000040  4c 40 40 59 41 3f 41 56  3f 24 43 53 74 72 69 6e  |L@@YA?AV?$CStrin|
00000050  67 54 40 5f 57 56 3f 24  53 74 72 54 72 61 69 74  |gT@_WV?$StrTrait|
00000060  4d 46 43 40 5f 57 56 3f  24 43 68 54 72 61 69 74  |MFC@_WV?$ChTrait|
00000070  73 43 52 54 40 5f 57 40  41 54 4c 40 40 40 40 40  |sCRT@_W@ATL@@@@@|
00000080  30 40 41 42 56 31 30 40  30 40 5a 00 5f 5f 75 6e  |0@ABV10@0@Z.__un|
00000090  77 69 6e 64 66 75 6e 63  6c 65 74 24 3f 3f 48 41  |windfunclet$??HA|
000000a0  54 4c 40 40 59 41 3f 41  56 3f 24 43 53 74 72 69  |TL@@YA?AV?$CStri|
000000b0  6e 67 54 40 5f 57 56 3f  24 53 74 72 54 72 61 69  |ngT@_WV?$StrTrai|
000000c0  74 4d 46 43 40 5f 57 56  3f 24 43 68 54 72 61 69  |tMFC@_WV?$ChTrai|
000000d0  74 73 43 52 54 40 5f 57  40 41 54 4c 40 40 40 40  |tsCRT@_W@ATL@@@@|
000000e0  40 30 40 41 42 56 31 30  40 30 40 5a 24 30 00 5f  |@0@ABV10@0@Z$0._|
000000f0  5f 65 68 68 61 6e 64 6c  65 72 24 3f 3f 48 41 54  |_ehhandler$??HAT|
00000100  4c 40 40 59 41 3f 41 56  3f 24 43 53 74 72 69 6e  |L@@YA?AV?$CStrin|
00000110  67 54 40 5f 57 56 3f 24  53 74 72 54 72 61 69 74  |gT@_WV?$StrTrait|
00000120  4d 46 43 40 5f 57 56 3f  24 43 68 54 72 61 69 74  |MFC@_WV?$ChTrait|
00000130  73 43 52 54 40 5f 57 40  41 54 4c 40 40 40 40 40  |sCRT@_W@ATL@@@@@|
00000140  30 40 41 42 56 31 30 40  50 42 5f 57 40 5a 00 5f  |0@ABV10@PB_W@Z._|
00000150  5f 75 6e 77 69 6e 64 66  75 6e 63 6c 65 74 24 3f  |_unwindfunclet$?|
00000160  3f 48 41 54 4c 40 40 59  41 3f 41 56 3f 24 43 53  |?HATL@@YA?AV?$CS|
00000170  74 72 69 6e 67 54 40 5f  57 56 3f 24 53 74 72 54  |tringT@_WV?$StrT|
00000180  72 61 69 74 4d 46 43 40  5f 57 56 3f 24 43 68 54  |raitMFC@_WV?$ChT|
00000190  72 61 69 74 73 43 52 54  40 5f 57 40 41 54 4c 40  |raitsCRT@_W@ATL@|
000001a0  40 40 40 40 30 40 41 42  56 31 30 40 50 42 5f 57  |@@@@0@ABV10@PB_W|
000001b0  40 5a 24 30 00 5f 5f 65  68 68 61 6e 64 6c 00 fe  |@Z$0.__ehhandl..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 88 f5 10 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 88  f5 10 6c ff 4b 04 00 00  |..........l.K...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```
What do I do next? Before I installation from DVD I made a separate partition to install ubuntu on ( 70GB, 4 in total, including hidden one that windows uses along with the NSA). 
In windows it shows only half of a partition that I used to installation (presumably the one that ubuntu defined as DATA), but it does not detect the system 'half' in any way.

All I wish for is ubuntu to boot properly and a starting screen that asks me which system I want to work on (As I do have on my good old XP).
Any help would be apprecitated.

---

### Post by oldfred on 2014-04-09
It does not look like grub installed at all.
I would try Boot-Repair, advanced where it purges & totally reinstalls grub. You do not need purge, but need the total reinstall of grub2.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by mastablasta on 2014-04-10
i hope this is not a wubi install inside windows...

and that you had max 3 primary partitions before attempted the install.

if all is good boot repair will solve the issue.

---

