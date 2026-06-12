---
title: "boot repair"
date: 2024-06-24
forum: Installation &amp; Upgrades
---

### Post by jooboi on 2024-06-24
the boot repi said to post this in forums im new
```
boot-repair-4ppa2075                                              [20240624_1819]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

nvme0n1p3: _____________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 


================================ 1 OS detected =================================

OS#1:   The OS now in use - Ubuntu 22.04.4 LTS on mapper/vguser-root

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: TigerLake-LP GT2 [Iris Xe Graphics] EFI VGA from Intel Corporation
BOOT_IMAGE of the installed session in use:
/vmlinuz-5.15.85-051585-generic root=/dev/mapper/vguser-root ro recovery nomodeset dis_ucode_ldr
df -Th / : /dev/mapper/vguser-root ext4  915G   25G  845G   3% /

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.36.0(1.36) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0006
Timeout: 5 seconds
BootOrder: 0006,0005,0000,0003,0004,0001
Boot0000* ONBOARD NIC (IPV4)    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(b04f13c96e3e,0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y.
Boot0001* UEFI RST MTFDHBK1T0TDP 22333C5C54A1     HD(1,GPT,3f2116eb-bd2b-4c2e-964d-c37075f1bb87,0x800,0x100000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0003* ONBOARD NIC (IPV6)    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(b04f13c96e3e,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.
Boot0004* UEFI HTTPs Boot    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(b04f13c96e3e,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()N.....YM....R,Y.
Boot0005* ll    PciRoot(0x0)/Pci(0x14,0x0)/USB(6,0)/HD(1,MBR,0x300edc3,0x80,0x1d4b720)/File(\EFI\BOOT\grubx64.efi)
Boot0006* ubuntu    HD(1,GPT,3f2116eb-bd2b-4c2e-964d-c37075f1bb87,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ok,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : is---sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 7E7A912C-EDCD-4D27-B717-9731F739B521
           Start        End    Sectors   Size Type
nvme0n1p1    2048    1050623    1048576   512M EFI System
nvme0n1p2 1050624    4050943    3000320   1.4G Linux filesystem
nvme0n1p3 4050944 2000408575 1996357632 951.9G Linux filesystem
Disk mapper/nvme0n1p3_crypt: 951.92 GiB, 1022118330368 bytes, 1996324864 sectors
Disk mapper/vguser-root: 930.37 GiB, 998974160896 bytes, 1951121408 sectors
Disk mapper/vguser-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Disk zram0: 3.76 GiB, 4033507328 bytes, 984743 sectors

parted -lm (filtered): _________________________________________________________

mapper/vguser-swap_1:1023MB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:1023MB:1023MB:linux-swap(v1)::;
mapper/vguser-root:999GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:999GB:999GB:ext4::;
mapper/nvme0n1p3_crypt:1022GB:dm:512:512:unknown:Linux device-mapper (crypt):;
nvme0n1:1024GB:nvme:512:512:gpt:MTFDHBK1T0TDP:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:2074MB:1536MB:ext4::;
3:2074MB:1024GB:1022GB:::;

blkid (filtered): ______________________________________________________________

NAME                FSTYPE      UUID                                   PARTUUID                             LABEL PARTLABEL
nvme0n1                                                                                                           
|-nvme0n1p1         vfat        BA29-72D1                              3f2116eb-bd2b-4c2e-964d-c37075f1bb87       EFI System Partition
|-nvme0n1p2         ext4        e3d2560d-8ce6-40b0-a4d5-85c00273f24e   35090133-7ee3-496e-94c0-69e5efecffaf       
`-nvme0n1p3         crypto_LUKS 5a581db2-37aa-417a-a4f3-187c1159f197   810331c1-f940-416c-bf70-118e77aeaa22       
  `-nvme0n1p3_crypt LVM2_member p2hfEf-07VC-KUGc-SnQL-VL0F-T415-AYScY9                                            
    |-vguser-root   ext4        7a33e7da-6280-4234-8877-5bfe2a6ed5aa                                              
    `-vguser-swap_1 swap        2b45cd0b-6fad-471b-a373-c029385a88bc                                              

Mount points (filtered): _______________________________________________________

                                              Avail Use% Mounted on
/dev/mapper/vguser-root                        844G   3% /
/dev/nvme0n1p2                                 1.2G   9% /boot

Mount options (filtered): ______________________________________________________

/dev/mapper/vguser-root                      ext4            rw,relatime,errors=remount-ro
/dev/nvme0n1p2                               ext4            rw,relatime

============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
nvme0n1p3_crypt
vguser-root
vguser-swap_1

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid e3d2560d-8ce6-40b0-a4d5-85c00273f24e root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

====================== nvme0n1p2/grub/grub.cfg (filtered) ======================

Ubuntu   7a33e7da-6280-4234-8877-5bfe2a6ed5aa
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###
Predator-OS, with Linux 5.15.85-051585-generic   7a33e7da-6280-4234-8877-5bfe2a6ed5aa
UEFI Firmware Settings   uefi-firmware

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
   0.651386261 = 0.699420672    grub/grub.cfg                                  1
   0.777336121 = 0.834658304    vmlinuz                                        1
   0.777336121 = 0.834658304    vmlinuz-5.15.85-051585-generic                 1
   0.930946350 = 0.999596032    initrd.img                                     2
   0.930946350 = 0.999596032    initrd.img-5.15.85-051585-generic              2
   0.930946350 = 0.999596032    initrd.img.old                                 2

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on nvme0n1p3



==================== blkid (filtered) before lvm activation ====================

/dev/mapper/nvme0n1p3_crypt: UUID="p2hfEf-07VC-KUGc-SnQL-VL0F-T415-AYScY9" TYPE="LVM2_member"
/dev/mapper/vguser-root: UUID="7a33e7da-6280-4234-8877-5bfe2a6ed5aa" BLOCK_SIZE="4096" TYPE="ext4"
/dev/nvme0n1p3: UUID="5a581db2-37aa-417a-a4f3-187c1159f197" TYPE="crypto_LUKS" PARTUUID="810331c1-f940-416c-bf70-118e77aeaa22"
/dev/nvme0n1p1: UUID="BA29-72D1" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="3f2116eb-bd2b-4c2e-964d-c37075f1bb87"
/dev/nvme0n1p2: UUID="e3d2560d-8ce6-40b0-a4d5-85c00273f24e" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="35090133-7ee3-496e-94c0-69e5efecffaf"
/dev/mapper/vguser-swap_1: UUID="2b45cd0b-6fad-471b-a373-c029385a88bc" TYPE="swap"
/dev/zram0: UUID="591200cc-5805-4590-8673-d876b6bc5fdf" TYPE="swap"


================================ LVM activation ================================

modprobe dm-mod  
vgscan --mknodes
  Found volume group "vguser" using metadata type lvm2
vgchange -ay
  2 logical volume(s) in volume group "vguser" now active
lvscan
  ACTIVE            '/dev/vguser/root' [<930.37 GiB] inherit
  ACTIVE            '/dev/vguser/swap_1' [976.00 MiB] inherit
blkid -g



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

Confirmation request before suggested repair: __________________________________

You may want to retry after mounting your encrypted partitions so that the tool can verify their contents. (cryptsetup open)
Are you sure you want to continue anyway?
```

---

### Post by oldfred on 2024-06-24
Better to follow Boot-Repair's instructions and just post link to summary report.
But if posting text or terminal output you need to use code tags.

Code Tags
[https://ubuntuforums.org/showthread.php?t=2497846](https://ubuntuforums.org/showthread.php?t=2497846)
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]
I use quote tags and then edit to be code.

Report is incomplete as you did not mount your encrypted partition. So Boot-Repair cannot see full system configuration.
Re-run report with encrypted mounted and post link.

---

### Post by grahammechanical on 2024-06-25
OK. We accept that you are new but what is the problem? What makes you think that Boot Repair could fix the problem? It is unusual for Boot Repair not to suggest a repair. The usual repair is to re-install Ubuntu boot loader files into the EFI System partition.

Regards

---

