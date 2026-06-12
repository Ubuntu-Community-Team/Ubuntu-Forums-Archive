---
title: "Need boot expert help to fix boot"
date: 2023-03-02
forum: Installation &amp; Upgrades
---

### Post by jsntcx on 2023-03-02
Dear Sir or Madam,

I have dual boot system with ubuntu 22.04 (upgraded from 20.04) and windows 11. 
I ran os-uninstaller to try to delete windows system in ubuntu 22.04, not from live CD :(
The system got stuck in some way and I had to restart the computer. Then it went to the grub prompt directly. 
I cannot find the boot under efi/ folder. so, I booted from a usb with ubuntu 20.04 image. I installed and ran boot-repair but it did not give a repair option. 
I created a BootInfo summary as below. Please help me how to get my boot back to boot into ubuntu 22.04, and if possible, how to uninstall windows and release the disk spaces into my ubuntu parition from the broken point.
My ubuntu is installed in /dev/nvme1n1p6.
   Thanks a lot! I really appreciate!

[https://paste.ubuntu.com/p/DRCZ2fKk9X/](https://paste.ubuntu.com/p/DRCZ2fKk9X/) or below:
```


boot-repair-4ppa203                                              [20230302_0731]

============================== Boot Info Summary ===============================

 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/nvme1n1.
 => No boot loader is installed in the MBR of /dev/sda.

nvme0n1p1: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme1n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/HP/BIOSUpdate/BiosMgmt32.efi 
                       /efi/HP/BIOSUpdate/BiosMgmt.efi 
                       /efi/HP/BIOSUpdate/CryptRSA32.efi 
                       /efi/HP/BIOSUpdate/CryptRSA.efi 
                       /efi/HP/BIOSUpdate/HpBiosMgmt32.efi 
                       /efi/HP/BIOSUpdate/HpBiosMgmt.efi 
                       /efi/HP/BIOSUpdate/HpBiosUpdate32.efi 
                       /efi/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /efi/HP/SystemDiags/CryptRSA.efi 
                       /efi/HP/SystemDiags/SysDiags.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

nvme1n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme1n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme1n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme1n1p5: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvme1n1p6: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Windows 10 or 11 on nvme1n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: NVIDIA Corporation from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: F.20(15.32) from AMI
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,0000,0001,0002,0004
Boot0000* Windows Boot Manager    HD(1,GPT,247dbf73-418a-40a9-9117-800c868ae2c8,0x800,0x82000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* UEFI:CD/DVD Drive    BBS(129,,0x0)
Boot0002* UEFI:Removable Device    BBS(130,,0x0)
Boot0003* ubuntu    HD(1,GPT,247dbf73-418a-40a9-9117-800c868ae2c8,0x800,0x82000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0004* UEFI:Network Device    BBS(131,,0x0)

728124f6ec8e22fbdbe7034812c81b95   nvme1n1p1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   nvme1n1p1/Boot/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme1n1p1/Boot/mmx64.efi
3795ef72a4ed0369ca44e711527904bf   nvme1n1p1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme1n1p1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme1n1p1/ubuntu/shimx64.efi
8d99cf85bc137151c9325b41fe4af2b7   nvme1n1p1/HP/BIOSUpdate/BiosMgmt32.efi
db7c40d52848fd1de511b3ad0a54ed88   nvme1n1p1/HP/BIOSUpdate/BiosMgmt.efi
1b8c0684ede8539ccc205cf7a750eca3   nvme1n1p1/HP/BIOSUpdate/CryptRSA32.efi
6488d391f74263c9da3c3d47dffa6212   nvme1n1p1/HP/BIOSUpdate/CryptRSA.efi
9303b09e6b77a2c51bb760d8394dfab2   nvme1n1p1/HP/BIOSUpdate/HpBiosMgmt32.efi
e4c4d6b9db9a7ceacaf24f4170c36718   nvme1n1p1/HP/BIOSUpdate/HpBiosMgmt.efi
a0037cbc3e9c787b8ef994f90c49899b   nvme1n1p1/HP/BIOSUpdate/HpBiosUpdate32.efi
1eff10b3253e2403e3e2cbd57b76eba5   nvme1n1p1/HP/BIOSUpdate/HpBiosUpdate.efi
6488d391f74263c9da3c3d47dffa6212   nvme1n1p1/HP/SystemDiags/CryptRSA.efi
a571b7ba1b94bf54a7dea327f9726b96   nvme1n1p1/HP/SystemDiags/SysDiags.efi
6baf5a5dd6571024320fa9ee09b3f7d9   nvme1n1p1/Microsoft/Boot/bootmgfw.efi
0d5069c1a8066904a58e0e91d13f9975   nvme1n1p1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
nvme1n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sda    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme1n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme1n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme1n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme1n1p6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme1n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme1n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme1n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme1n1p6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme1n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
nvme1n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
nvme1n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
nvme1n1p6    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
sda1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk nvme1n1: 953.89 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 0A124344-4FB7-44DE-9FA5-041C212DEE7D
               Start        End   Sectors   Size Type
nvme1n1p1       2048     534527    532480   260M EFI System
nvme1n1p2     534528     567295     32768    16M Microsoft reserved
nvme1n1p3     567296  950685695 950118400 453.1G Microsoft basic data
nvme1n1p4 1999261696 2000396287   1134592   554M Windows recovery environment
nvme1n1p5  950685696 1014685695  64000000  30.5G Linux swap
nvme1n1p6 1014685696 1999261695 984576000 469.5G Linux filesystem
Partition table entries are not in disk order.
Disk nvme0n1: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 32B08B13-04DF-4522-9A42-C5BA17062BD9
          Start        End    Sectors  Size Type
nvme0n1p1  2048 3907028991 3907026944  1.8T Linux filesystem
Disk sda: 7.28 TiB, 8001563222016 bytes, 15628053168 sectors
Disk identifier: 71124B4A-D49B-49BA-9140-A8ACF245D27D
      Start         End     Sectors  Size Type
sda1   2048 15628052479 15628050432  7.3T Linux filesystem
Disk sdb: 7.47 GiB, 8004304896 bytes, 15633408 sectors
Disk identifier: 0x2cf4ba3a
      Boot   Start      End Sectors  Size Id Type
sdb1  *          0  5999871 5999872  2.9G  0 Empty
sdb2       5271500  5279499    8000  3.9M ef EFI (FAT-12/16/32)
sdb3       6000640 15633407 9632768  4.6G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:8002GB:scsi:512:4096:gpt:ATA ST8000DM004-2CX1:;
1:1049kB:8002GB:8002GB:ext4::;
sdb:8004MB:scsi:512:512:unknown:SanDisk Cruzer Blade:;
nvme0n1:2000GB:nvme:512:512:gpt:Samsung SSD 970 EVO Plus 2TB:;
1:1049kB:2000GB:2000GB:ext4::;
nvme1n1:1024GB:nvme:512:512:gpt:WDC WD BLACK SDBPNTY-1T00-1106:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:487GB:486GB:ntfs:Basic data partition:msftdata;
5:487GB:520GB:32.8GB:linux-swap(v1)::swap;
6:520GB:1024GB:504GB:ext4::;
4:1024GB:1024GB:581MB:ntfs:Basic data partition:hidden, diag;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                     
&#9492;&#9472;sda1      ext4     74d45653-9d41-43ee-8a0d-3f139a93803f 7e7b11af-7857-4548-be3d-120bbf93a3d2                          
sdb         iso9660  2021-08-19-11-03-38-00                                                    Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb1      iso9660  2021-08-19-11-03-38-00               2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb2      vfat     54C5-9C6C                            2cf4ba3a-02                                                   
&#9492;&#9472;sdb3      ext4     310c27a3-b753-41e2-b4dd-2f610eeaa02e 2cf4ba3a-03                          writable                 
nvme1n1                                                                                                                 
&#9500;&#9472;nvme1n1p1 vfat     92D3-80E4                            247dbf73-418a-40a9-9117-800c868ae2c8 SYSTEM                   EFI system partition
&#9500;&#9472;nvme1n1p2                                               da1c806c-e56e-47db-8add-811cacbf5121                          Microsoft reserved partition
&#9500;&#9472;nvme1n1p3 ntfs     D6A44C6DA44C51E3                     3a3323e9-0182-4d6c-9fa7-6acd62fe6a81 Windows                  Basic data partition
&#9500;&#9472;nvme1n1p4 ntfs     94DED58CDED56750                     96e9abe8-345d-4ce7-ba52-74fa5789f52d Windows RE tools         Basic data partition
&#9500;&#9472;nvme1n1p5 swap     7e68a54a-4335-4414-9a08-48141afdb17a c1ed9283-4744-4955-a1c2-f93bcb9b9ef4                          
&#9492;&#9472;nvme1n1p6 ext4     7583c209-6b45-4700-bd71-375af4f59c0b 30b81cde-67a3-4838-a35f-118e70613261                          
nvme0n1                                                                                                                 
&#9492;&#9472;nvme0n1p1 ext4     ac7b2877-f57e-4a5b-a7e9-2011a30261f2 e707aa95-8cec-4179-afc1-20ea000ed401 nvme                     

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2023-03-02.1/crash]   4.2G   1% /var/crash
/dev/disk/by-label/writable[/install-logs-2023-03-02.1/log]     4.2G   1% /var/log
/dev/nvme0n1p1                                                  1.6T   7% /mnt/boot-sav/nvme0n1p1
/dev/nvme1n1p1                                                165.7M  35% /mnt/boot-sav/nvme1n1p1
/dev/nvme1n1p3                                                383.7G  15% /mnt/boot-sav/nvme1n1p3
/dev/nvme1n1p4                                                 66.9M  88% /mnt/boot-sav/nvme1n1p4
/dev/nvme1n1p6                                                  9.7G  93% /mnt/boot-sav/nvme1n1p6
/dev/sda1                                                       4.9T  27% /mnt/boot-sav/sda1
/dev/sdb1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________


=================== nvme1n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 7583c209-6b45-4700-bd71-375af4f59c0b root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sdb




Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  win-legacy-basic-fix

```

---

### Post by tea for one on 2023-03-02
Boot-repair has only detected one OS
[COLOR="#0000FF"]Line 93[/COLOR] - OS#1:   Windows 10 or 11 on nvme1n1p3

I'm not familiar with os-uninstaller so I don't know how it works or even if it is compatible with UEFI systems..
Windows seems to exist and Ubuntu is missing.

[COLOR="#0000FF"]Line 5[/COLOR] - Windows 7/8/10/11/2012 is installed in the MBR of /dev/nvme0n1
[COLOR="#0000FF"]Line 36[/COLOR] - /efi/Microsoft/Boot/bootmgfw.efi 

If you boot in EFI mode, there should not be an mbr entryfor Windows 11 in line 5.

Do you have backups?
Can you boot into Windows?

---

### Post by yancek on 2023-03-02
The boot repair output under partition info shows no OS, no Grub and no fstab on partition 6 where Ubuntu is/was installed.  Probably due to the software not finishing due to the freeze.  If you want to remove the windows partitions, there is no need for software such as you used, you simply format the windows partitions with the exception of the EFI/vfat partition.

When you ran boot repair, did you boot the USB in EFI mode?

---

### Post by jsntcx on 2023-03-02
No, I do not have backups. :(

I found /deleted_os folder in (hd2,gpt6) in grub terminal. It seems that all ubuntu os were moved into the folder. Should I just move them back to /?
Btw, the disk availability of nvme1n1p6 is the same before the accident. So, is there a way to recover the ubuntu os first and then fix the boot?


I cannot boot into windows either. It showed me a blue screen with damaged boot notice.

---

### Post by jsntcx on 2023-03-02
I think I booted usb in UEFI mode because I checked [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy" and it turned UEFI.

---

### Post by jsntcx on 2023-03-02
I am trying testdisk. The following is my damaged ubuntu os partition. What should I do? Should I mark "Linux filesys. data" as P (partition) and confirm to "Write"? I have no idea how testdisk works. Please kindly help. Thanks a lot!


[IMG]https://ibb.co/DCjSTmX[/IMG]
[IMG]https://ibb.co/DCjSTmX[/IMG]

---

### Post by pavelshtykov on 2024-01-13
Hi! I have exactly the same problem as you! How did you solve it?..

---

