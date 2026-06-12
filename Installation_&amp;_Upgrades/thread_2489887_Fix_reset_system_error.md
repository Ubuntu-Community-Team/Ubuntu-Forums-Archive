---
title: "Fix reset system error"
date: 2023-08-13
forum: Installation &amp; Upgrades
---

### Post by coolqiqi1781 on 2023-08-13
I installed Ubuntu on my Lenovo IdeaPad 1 14IGL05, however whenever i try to boot up Ubuntu, it just turns on, say "reset system" then turn off. I followed a guide to fix the error, so here is the boot log. Note that I am using Ubuntu 22.04.3 LTS. Boot log->boot-repair-4ppa2056                                              [20230813_1437]

```
============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/mmcblk0.
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------

mmcblk0p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

mmcblk0p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04.2 LTS on mmcblk0p2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GeminiLake [UHD Graphics 600] from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.2 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: DWCN27WW(1.27) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled.
BootCurrent: 0019
Timeout: 0 seconds
BootOrder: 0001,0000,0013,0014,0015,0016,0017,0018,0019
Boot0000* Windows Boot Manager    HD(1,GPT,8e838157-aa75-40f7-b2d1-b2956b37abc9,0x800,0x100000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...}................
Boot0001* ubuntu    HD(1,GPT,4454e52c-dc09-4423-bd9d-51f25964a05d,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0010  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu    FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)
Boot0012  Diagnostic Splash    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013* NVMe:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a4)
Boot0014* eMMC Card: Ramaxel  64GB    PciRoot(0x0)/Pci(0x1c,0x0)/eMMC(0)/Ctrl(0x0)c.J8.p[H...S....
Boot0015* USB HDD: Generic- SD/MMC/MS PRO    PciRoot(0x0)/Pci(0x15,0x0)/USB(7,0)3.!..3.G..A.....
Boot0016* USB FDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0017* USB CD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0018* USB LAN:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322)
Boot0019* USB HDD: UFD 3.0 Silicon-Power16G    PciRoot(0x0)/Pci(0x15,0x0)/USB(10,0)3.!..3.G..A.....

64349b3622c65f495a99dbf6102496e3   mmcblk0p1/BOOT/bkpbootx64.efi
64349b3622c65f495a99dbf6102496e3   mmcblk0p1/BOOT/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   mmcblk0p1/BOOT/fbx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   mmcblk0p1/BOOT/grubx64.efi
a660182adef313615746a665966d2ccc   mmcblk0p1/BOOT/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   mmcblk0p1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   mmcblk0p1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   mmcblk0p1/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   sdb1/boot/bootx64.efi
dbb73486aa1fffa648f99f31f209f545   sdb1/boot/grubx64.efi
a660182adef313615746a665966d2ccc   sdb1/boot/mmx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

mmcblk0    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    mmc-disk, has-os,    no-wind,    1 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has---ESP,     liveusb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

mmcblk0p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
mmcblk0p2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    not-far
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

mmcblk0p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
mmcblk0p2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

mmcblk0p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    mmcblk0
mmcblk0p2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    mmcblk0
sdb1    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk mmcblk0: 58.24 GiB, 62537072640 bytes, 122142720 sectors
Disk identifier: 8EE83A4C-0E28-48CF-BF4A-11F40362EE5E
            Start       End   Sectors  Size Type
mmcblk0p1    2048   1050623   1048576  512M EFI System
mmcblk0p2 1050624 122140671 121090048 57.7G Linux filesystem
Disk mmcblk0boot0: 4 MiB, 4194304 bytes, 8192 sectors
Disk mmcblk0boot1: 4 MiB, 4194304 bytes, 8192 sectors
Disk sda: 14.57 GiB, 15644753920 bytes, 30556160 sectors
Disk identifier: 0x05371705
      Boot Start      End  Sectors  Size Id Type
sda1  *     2048 30556159 30554112 14.6G  c W95 FAT32 (LBA)
Disk sdb: 58.24 GiB, 62534975488 bytes, 122138624 sectors
Disk identifier: 0x00040ed1
      Boot Start       End   Sectors  Size Id Type
sdb1  *     2048 122138623 122136576 58.2G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:15.6GB:scsi:512:512:msdos:UFD 3.0 Silicon-Power16G:;
1:1049kB:15.6GB:15.6GB:fat32::boot, lba;
sdb:62.5GB:scsi:512:512:msdos:Generic- SD/MMC/MS PRO:;
1:1049kB:62.5GB:62.5GB:fat32::boot, lba;
mmcblk0:62.5GB:sd/mmc:512:512:gpt:MMC MMC64G:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:62.5GB:62.0GB:ext4::;
mmcblk0boot0:4194kB:sd/mmc:512:512:unknown:Generic SD/MMC Storage Card:;
mmcblk0boot1:4194kB:sd/mmc:512:512:unknown:Generic SD/MMC Storage Card:;

blkid (filtered): ______________________________________________________________

NAME         FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                         
&#9492;&#9472;sda1       vfat     50DB-EF95                            05371705-01                          UBUNTU 22_0 
sdb                                                                                                         
&#9492;&#9472;sdb1       vfat     17FA-371A                            00040ed1-01                                      
mmcblk0                                                                                                     
&#9500;&#9472;mmcblk0p1  vfat     A11C-6D97                            4454e52c-dc09-4423-bd9d-51f25964a05d             EFI System Partition
&#9492;&#9472;mmcblk0p2  ext4     fbcd7387-8655-41fa-8583-c65ca8a5f0f1 f1b3f2d3-6fa6-4899-b697-ec7f8e7fc8b9             
mmcblk0boot0                                                                                                
mmcblk0boot1                                                                                                

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/mmcblk0p1            501.5M   2% /mnt/boot-sav/mmcblk0p1
/dev/mmcblk0p2             40.5G  23% /mnt/boot-sav/mmcblk0p2
/dev/sda1                    10G  32% /cdrom
/dev/sdb1                  53.6G   8% /media/ubuntu/17FA-371A

Mount options (filtered): ______________________________________________________


=================== mmcblk0p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid fbcd7387-8655-41fa-8583-c65ca8a5f0f1 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== mmcblk0p2/boot/grub/grub.cfg (filtered) ====================

Ubuntu   fbcd7387-8655-41fa-8583-c65ca8a5f0f1
Ubuntu, with Linux 6.2.0-26-generic   fbcd7387-8655-41fa-8583-c65ca8a5f0f1
Ubuntu, with Linux 5.19.0-32-generic   fbcd7387-8655-41fa-8583-c65ca8a5f0f1
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

======================== mmcblk0p2/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/mmcblk0p2 during installation
UUID=fbcd7387-8655-41fa-8583-c65ca8a5f0f1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/mmcblk0p1 during installation
UUID=A11C-6D97  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

==================== mmcblk0p2/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= mmcblk0p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
  46.386619568 = 49.807253504   boot/grub/grub.cfg                             1
  56.670047760 = 60.849000448   boot/vmlinuz                                   2
   8.356075287 = 8.972267520    boot/vmlinuz-5.19.0-32-generic                 1
  56.670047760 = 60.849000448   boot/vmlinuz-6.2.0-26-generic                  2
   8.356075287 = 8.972267520    boot/vmlinuz.old                               1
  35.836025238 = 38.478639104   boot/initrd.img                                1
  35.512424469 = 38.131175424   boot/initrd.img-5.19.0-32-generic              1
  35.836025238 = 38.478639104   boot/initrd.img-6.2.0-26-generic               1
  35.512424469 = 38.131175424   boot/initrd.img.old                            1

=================== mmcblk0p2: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec  2  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec  2  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec  2  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec  2  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Sep 20  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Dec  2  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec  2  2022 41_custom

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
mmcblk0p2,
using the following options:  mmcblk0p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.2 LTS entry (mmcblk0p1/efi/****/shim****.efi (**** will be updated in the final message) file) !
```

---

### Post by tea for one on 2023-08-13
Power on and access your UEFI settings via F2
Disable Secure Boot
Disable TPM
Disable Platform Trust Technology (and/or similar settings concerning Trust)
Save and exit UEFI settings

Hopefully, Ubuntu 22.04 will appear?

---

### Post by coolqiqi1781 on 2023-08-13
Thank you so much! I was able to get into the menu and log on to Ubuntu.

---

### Post by tea for one on 2023-08-13
Pleased to have helped.

It is a nice gesture to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads).

---

