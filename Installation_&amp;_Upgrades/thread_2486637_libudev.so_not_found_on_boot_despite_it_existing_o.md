---
title: "libudev.so not found on boot despite it existing on hard drive"
date: 2023-05-07
forum: Installation &amp; Upgrades
---

### Post by john44442 on 2023-05-07
[http://paste.ubuntu.com/p/wFjpdcHFsr/](http://paste.ubuntu.com/p/wFjpdcHFsr/)

```

boot-repair-4ppa203                                              [20230507_0654]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bootx64.efi /efi/BOOT/fbx64.efi 
                       /efi/BOOT/grubx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /grub/i386-pc/core.img 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


================================ 1 OS detected =================================

OS#1:   Ubuntu 20.04.5 LTS on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: UHD Graphics 620 from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 18.04.3 LTS, bionic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 7.13 from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0003,0004,0001,0002,0000
Boot0000  ubuntu    HD(1,GPT,6a873292-8347-4515-91f5-5da154a17e34,0x800,0x100000)/File(\EFI\UBUNTU\GRUBX64.EFI)
Boot0001  UEFI: PXE IP4 Realtek PCIe GBE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x1)/MAC(80fa5b75b0d0,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0002  UEFI: PXE IP6 Realtek PCIe GBE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x1)/MAC(80fa5b75b0d0,0)/IPv6([::]:<->[::]:,0,0)..BO
Boot0003* ubuntu    HD(1,GPT,6a873292-8347-4515-91f5-5da154a17e34,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0004* UEFI: USB DISK 2.0 1219, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(5,0)/HD(1,MBR,0x24bd07,0x800,0x777800)..BO

6c168a33842e0b683118cd53ff8a12e0   sda1/BOOT/bootx64.efi
5dabe049a4dad758d975dc2e60a7f00e   sda1/BOOT/fbx64.efi
64a633007e3d5a9a5943e417442548d6   sda1/BOOT/grubx64.efi
b87d854e443e7fe6609397a3e5bfb74b   sda1/ubuntu/grubx64.efi
f243a42f3bd3164872e792dbc2610270   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ok,    noupdategrub,    not-far
sda2    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ng,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: 40FBC645-A4A8-4371-AF9E-4DEB29AEC0E4
        Start       End   Sectors   Size Type
sda1     2048   1050623   1048576   512M EFI System
sda2  1050624 234440703 233390080 111.3G Linux filesystem
Disk sdb: 3.8 GiB, 4009754624 bytes, 7831552 sectors
Disk identifier: 0x0024bd07
      Boot Start     End Sectors  Size Id Type
sdb1  *     2048 7831551 7829504  3.8G  c W95 FAT32 (LBA)
Disk zram0: 995 MiB, 1043312640 bytes, 254715 sectors
Disk zram1: 995 MiB, 1043312640 bytes, 254715 sectors
Disk zram2: 995 MiB, 1043312640 bytes, 254715 sectors
Disk zram3: 995 MiB, 1043312640 bytes, 254715 sectors
Disk zram4: 995 MiB, 1043312640 bytes, 254715 sectors
Disk zram5: 995 MiB, 1043312640 bytes, 254715 sectors
Disk zram6: 995 MiB, 1043312640 bytes, 254715 sectors
Disk zram7: 995 MiB, 1043312640 bytes, 254715 sectors

parted -lm (filtered): _________________________________________________________

sda:120GB:scsi:512:512:gpt:ATA ADATA SU650:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:120GB:119GB:ext4::;
sdb:4010MB:scsi:512:512:msdos:USB DISK 2.0:;
1:1049kB:4010MB:4009MB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1 vfat     BC0A-E8A5                            6a873292-8347-4515-91f5-5da154a17e34             EFI System Partition
&#9492;&#9472;sda2 ext4     67a5b64c-cd86-400b-9a32-443206011cf3 fc41a4ba-a5c0-4f15-a98d-a50b70a0de37             
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     3021-403A                            0024bd07-01                          LUBUNTU 18_ 

Mount points (filtered): _______________________________________________________

             Avail Use% Mounted on
/dev/sda1   492.5M   4% /mnt/boot-sav/sda1
/dev/sda2     6.8G  89% /mnt/boot-sav/sda2
/dev/sdb1     2.7G  29% /cdrom

Mount options (filtered): ______________________________________________________


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 67a5b64c-cd86-400b-9a32-443206011cf3 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             grub/i386-pc/core.img                          1
            ?? = ??             boot/grub/i386-pc/core.img                     1

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   67a5b64c-cd86-400b-9a32-443206011cf3
Ubuntu, with Linux 5.4.0-144-generic   67a5b64c-cd86-400b-9a32-443206011cf3
Ubuntu, with Linux 5.4.0-137-generic   67a5b64c-cd86-400b-9a32-443206011cf3
Ubuntu, with Linux 5.4.0-136-generic   67a5b64c-cd86-400b-9a32-443206011cf3
Ubuntu, with Linux 5.4.0-120-generic   67a5b64c-cd86-400b-9a32-443206011cf3
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=67a5b64c-cd86-400b-9a32-443206011cf3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=BC0A-E8A5  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

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
  96.699222565 = 103.829999616  boot/grub/grub.cfg                             3
  19.474655151 = 20.910751744   boot/vmlinuz                                   1
  22.755897522 = 24.433958912   boot/vmlinuz-5.4.0-120-generic                 1
  22.841831207 = 24.526229504   boot/vmlinuz-5.4.0-136-generic                 1
  22.318393707 = 23.964192768   boot/vmlinuz-5.4.0-137-generic                 1
  19.474655151 = 20.910751744   boot/vmlinuz-5.4.0-144-generic                 1
  22.318393707 = 23.964192768   boot/vmlinuz.old                               1
  22.841831207 = 24.526229504   vmlinuz                                        1
  24.024410248 = 25.796014080   boot/initrd.img                                6
  23.929065704 = 25.693638656   boot/initrd.img-5.4.0-120-generic              1
  23.878273010 = 25.639100416   boot/initrd.img-5.4.0-136-generic              2
  95.520656586 = 102.564524032  boot/initrd.img-5.4.0-137-generic              3
  24.024410248 = 25.796014080   boot/initrd.img-5.4.0-144-generic              6
  95.520656586 = 102.564524032  boot/initrd.img.old                            3
  23.878273010 = 25.639100416   initrd.img                                     2

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18224 Dec  2 15:20 10_linux
-rwxr-xr-x 1 root root 42359 Dec  2 15:20 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Dec  2 15:20 20_linux_xen
-rwxr-xr-x 1 root root 12059 Nov 15 11:13 30_os-prober
-rwxr-xr-x 1 root root  1424 Dec  2 15:20 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Jul  3  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Nov 15 11:13 40_custom
-rwxr-xr-x 1 root root   216 Nov 15 11:13 41_custom

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Try Lubuntu without installing
Install Lubuntu
OEM install (for manufacturers)
Check disc for defects

========================= sdb1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to unsign) and reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.5 LTS entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !




```

What happens when I try and boot:

[https://i.imgur.com/3h0oNmb.jpg](https://i.imgur.com/3h0oNmb.jpg)

[https://i.imgur.com/WdE6wep.jpg](https://i.imgur.com/WdE6wep.jpg)

---

