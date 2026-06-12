---
title: "Ubuntu/Windows 11 Dual Boot Error (Grub terminal appears)"
date: 2023-05-28
forum: Installation &amp; Upgrades
---

### Post by arinaldi2204 on 2023-05-28
[View raw]("https://paste.ubuntu.com/p/JmfPCM4TQS/plain/")     

   Hi,
I am contacting you because i am having trouble starting my Ubuntu system from my dual boot computer (Windows 11, Ubuntu).
The problem is that, every time i try to boot the system from the Hard disk where Ubuntu is installed, the only thing that appears is the GRUB terminal (NOT in rescue mode).
I tried to manually boot various vmlinuz/initrd configurations but the boot always stops at an initramfs error.
At the moment Windows 11 and Ubuntu are installed on two different physical disks.
You can find my boot-repair error report below.

Thanks in advance for every help you'll be able to give me.
Andrea.


```

boot-repair-4ppa2056                                              [20230528_1630]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdd.
 => No known boot loader is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.2 LTS
    Boot files:        /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/grubx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/cbmr_driver.efi

sdc2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe

sdc4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.2 LTS on sda2
OS#2:   Windows 7 on sdc3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GA102 [GeForce RTX 3080 12GB] AlderLake-S GT1 from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.2 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.10(5.24) from American Megatrends International, LLC.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0000,0002,0003
Boot0000* Windows Boot Manager    HD(1,GPT,c2153c56-5c45-4174-ab73-406887a6425f,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0002* ubuntu    HD(1,GPT,c2153c56-5c45-4174-ab73-406887a6425f,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0003* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(7,0)/HD(1,GPT,d3bd69a2-c616-472e-a8a0-1964dc602289,0x800,0x1ca37df)..BO

5ddf997e8b025bfbc2009e85b32f60dc   sdc1/Boot/bkpbootx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   sdc1/Boot/bootx64.efi
2895d47544fd587b26c7e29be1295c27   sdc1/Boot/fbx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sdc1/Boot/grubx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sdc1/Boot/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   sdc1/ubuntu/grubx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sdc1/ubuntu/mmx64.efi
78415fb8fb9b909f8029858113f1335f   sdc1/ubuntu/shimx64.efi
226dd35eecb9c94a5e2f6defe862645a   sdc1/Microsoft/Boot/bootmgfw.efi
e8202499ef13b06fdda52341f8e5362e   sdc1/Microsoft/Boot/bootmgr.efi
b8796e68099026aabcebb8fcf75b21f6   sdc1/Microsoft/Boot/cbmr_driver.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sdd    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdc1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdc4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdd1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot
sdc4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sdd1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdd1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdd

fdisk -l (filtered): ___________________________________________________________

Disk sda: 447.13 GiB, 480103981056 bytes, 937703088 sectors
Disk identifier: 0x5169a811
      Boot   Start       End   Sectors   Size Id Type
sda1          2048   7999487   7997440   3.8G 82 Linux swap / Solaris
sda2  *    7999488 937701375 929701888 443.3G 83 Linux
Disk sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 0x9d9628a9
      Boot Start        End    Sectors  Size Id Type
sdb1        2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT
Disk sdc: 232.89 GiB, 250059350016 bytes, 488397168 sectors
Disk identifier: 4644CA4D-A09F-4ABA-B141-CFF7A354A413
          Start       End   Sectors   Size Type
sdc1       2048    206847    204800   100M EFI System
sdc2     206848    239615     32768    16M Microsoft reserved
sdc3     239616 486985250 486745635 232.1G Microsoft basic data
sdc4  486985728 488392703   1406976   687M Windows recovery environment
Disk sdd: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x0301dbd3
      Boot Start        End    Sectors   Size Id Type
sdd1        2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT
Disk sde: 14.32 GiB, 15376318464 bytes, 30031872 sectors
Disk identifier: 0F0845E5-53DA-4A6B-A73D-1AEF5AF5F675
      Start      End  Sectors  Size Type
sde1   2048 30031838 30029791 14.3G Microsoft basic data

parted -lm (filtered): _________________________________________________________

sda:480GB:scsi:512:512:msdos:ATA KINGSTON SA400S3:;
1:1049kB:4096MB:4095MB:linux-swap(v1)::;
2:4096MB:480GB:476GB:ext4::boot;
sdb:2000GB:scsi:512:4096:msdos:ATA WDC WD20EZRX-00D:;
1:1049kB:2000GB:2000GB:ntfs::;
sdc:250GB:scsi:512:512:gpt:ATA Samsung SSD 850:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:249GB:249GB:ntfs:Basic data partition:msftdata;
4:249GB:250GB:720MB:ntfs::hidden, diag;
sdd:1000GB:scsi:512:512:msdos:ATA SanDisk SDSSDH3:;
1:1049kB:1000GB:1000GB:ntfs::;
sde:15.4GB:scsi:512:512:gpt:SanDisk Cruzer Blade:;
1:1049kB:15.4GB:15.4GB:fat32:Main Data Partition:msftdata;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1 swap     4d2f9bf9-2a45-4726-9f9e-d5bbd8da3d8a 5169a811-01                                      
&#9492;&#9472;sda2 ext4     17733a58-d5ca-4ca6-be1e-06310e4d2b59 5169a811-02                                      
sdb                                                                                                   
&#9492;&#9472;sdb1 ntfs     2EFA8D00FA8CC595                     9d9628a9-01                          Storage     
sdc                                                                                                   
&#9500;&#9472;sdc1 vfat     1AC8-437D                            c2153c56-5c45-4174-ab73-406887a6425f             EFI system partition
&#9500;&#9472;sdc2                                               4e98c634-1f41-41d1-ba04-0d28e0c92836             Microsoft reserved partition
&#9500;&#9472;sdc3 ntfs     C4D8C913D8C90520                     c26cf25b-e648-4c9e-9ae6-95bd98349745             Basic data partition
&#9492;&#9472;sdc4 ntfs     84D62262D62254A8                     84624beb-2d90-4ab3-97ab-6b2d7bdecb64             
sdd                                                                                                   
&#9492;&#9472;sdd1 ntfs     6EB47F4FB47F1933                     0301dbd3-01                                      
sde                                                                                                   
&#9492;&#9472;sde1 vfat     C2D7-08CF                            d3bd69a2-c616-472e-a8a0-1964dc602289 UBUNTU 22_0 Main Data Partition

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/sda2                   340G  17% /mnt/boot-sav/sda2
/dev/sdb1                   1.4T  25% /mnt/boot-sav/sdb1
/dev/sdc1                  53.1M  45% /mnt/boot-sav/sdc1
/dev/sdc3                 126.6G  45% /mnt/boot-sav/sdc3
/dev/sdc4                  88.9M  87% /mnt/boot-sav/sdc4
/dev/sdd1                 473.3G  49% /mnt/boot-sav/sdd1
/dev/sde1                   9.7G  32% /cdrom

Mount options (filtered): ______________________________________________________


========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=17733a58-d5ca-4ca6-be1e-06310e4d2b59 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=4d2f9bf9-2a45-4726-9f9e-d5bbd8da3d8a none            swap    sw              0       0
UUID=1AC8-437D  /boot/efi       vfat    defaults      0       1

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  41.380500793 = 44.431974400   boot/vmlinuz                                   1
 354.400386810 = 380.534517760  boot/vmlinuz-5.15.0-72-generic                 2
 317.489871979 = 340.902154240  boot/vmlinuz-5.19.0-41-generic                 2
  41.380500793 = 44.431974400   boot/vmlinuz-5.19.0-42-generic                 1
 354.400386810 = 380.534517760  boot/vmlinuz.old                               2
  76.939449310 = 82.613104640   boot/initrd.img                                5
 120.298824310 = 129.169879040  boot/initrd.img-5.15.0-72-generic              3
  79.804344177 = 85.689262080   boot/initrd.img-5.19.0-41-generic              3
  76.939449310 = 82.613104640   boot/initrd.img-5.19.0-42-generic              5
 120.298824310 = 129.169879040  boot/initrd.img.old                            3

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================


===================== sdc1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 17733a58-d5ca-4ca6-be1e-06310e4d2b59 root hd0,msdos2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sde1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sde1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda2,
using the following options:  sdc1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.2 LTS entry (sdc1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)

```

---

### Post by yancek on 2023-05-28
You need to set sdc, the 1TB drive, to first boot priority in the BIOS firmware.  Your boot repair output shows an EFI install of Ubuntu as well as windows.  Although Ubuntu is on sda, its EFI boot files are on the EFI partition with windows (sdc).  You should be able to make a selection here in the BIOS boot options for windows or Ubuntu.

---

### Post by oldfred on 2023-05-28
You have an UEFI system and UEFI install of Windows.
And then need to be consistent, always use UEFI. BIOS boot loaders then confuse boot.
So have system to set to default boot in UEFI mode and only choose to boot flash drives in UEFI mode.

And better to always use gpt partitioning. Microsoft requires gpt for UEFI boot and has since 2012.
Ubuntu will let you use UEFI with MBR(msdos from 1980's) but really should not.
Converting drive from MBR to gpt will erase drive, so good backups required.

---

### Post by ajohnl on 2023-05-28
I've had a boot problem. Windows not on the machine, several flavours of Ubuntu and installed on a brand new disk. The bios was set to use UEF1 but Ubuntu's boot selection menu refused to come up. When I booted the last installed version just came up. Installing another distro that I know produces a boot selection menu didn't result in any change.

The main problem was that a disk boot was marked active in efi. This suggest that an mbr boot was being used. As I had only installed Ubuntu's when this started happening I have to assume they wrote to mbr. Once I disabled the disk boot using efibootmgr the machine booted to the different distro's menu which showed all of the Ubuntu's and I could boot to any of them. I used efibootmgr to set priorities. Then used that to put Ubuntu first again and it didn't show a menu. Just fell through to one of them.

Your problem may be the same. down to a disk boot being enabled in efi. It appears this can over ride the usual efi boot orders. In fact in my case if I deleted the last installed Ubuntu efi entry the bios recreated it as soon as the machine was booted again. Same making it active after I had set it inactive. Always the last Ubuntu installed. :) Sort of perverted secure boot but that wasn't enabled in the bios. I suspect it worked this way to ensure windows always booted even if things were changed but efi entries can be created from mbr entries, Both are just pointers to some part of the disk.

One other installs under UEFI I have tried to create another efi partition on a different disk. ;) not surprisingly the install just wouldn't have it. There can only be one and if windows is installed that way it has to be on that disk. You can mount / and swap etc to what ever disk you like. You can also install to an existing EFI partition but don't format it. It will just add an entry.

This machine with it's original disk in it also ran windows. It was set up for an MBR boot. It seems that win 8 and 10 and maybe 11 can be installed that way. When I installed Ubuntu on that it chose to install MBR style. This caused me even more confusion as I expected UEFI but each OS could be selected from a menu following a boot.

---

### Post by arinaldi2204 on 2023-05-30
Guys, thank you very much for your kind answers.
I'll try your suggestions as soon as possible and post back here the results.

---

