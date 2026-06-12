---
title: "Dual Boot HS after power outage"
date: 2023-10-29
forum: Installation &amp; Upgrades
---

### Post by james64000 on 2023-10-29
Good morning,

I'm coming back to you because following a power outage I lost my dual boot,

My NVME disk has two partitions.
250 GB for Windows 10.
250 GB for Ubuntu.

No longer able to boot on either partition (bios display at startup) I resigned myself to reinstalling Windows on its original partition.
From an Ubuntu USB key, I was able to access the data from my Ubuntu installation and I recovered my data.

I tried with Boot Repair Disk.
Once the process is finished, I get this error message:

An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please point this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Please write the following URL on a piece of paper:
[https://paste.ubuntu.com/p/sDRtcjfdck/](https://paste.ubuntu.com/p/sDRtcjfdck/)
If you still have startup problems, point this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Locked-NVram detected.

Here is the content of the paste:

```

boot-repair-4ppa2056                                              [20231029_0907]

============================= Boot Repair Summary ==============================





modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
ls: impossible d'accéder à '/sys/firmware/efi/vars': Aucun fichier ou dossier de ce type

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p5,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /mnt/boot-sav/nvme0n1p1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/nvme0n1p1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/nvme0n1p1/efi/Boot/bootx64.efi
Mount nvme0n1p1 on /mnt/boot-sav/nvme0n1p5/boot/efi

===================== Reinstall the grub-efi of nvme0n1p5 ======================

chroot /mnt/boot-sav/nvme0n1p5 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
chroot /mnt/boot-sav/nvme0n1p5 modprobe efivars

chroot /mnt/boot-sav/nvme0n1p5 efibootmgr -v before grub install
EFI variables are not supported on this system.


chroot /mnt/boot-sav/nvme0n1p5 uname -r
6.2.0-26-generic

chroot /mnt/boot-sav/nvme0n1p5 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
Refind detected on nvme0n1p1
cp /mnt/boot-sav/nvme0n1p5/boot/efi/efi/ubuntu/grubx64.efi /media/ubuntu/ESD-USB/efi/ubuntu/grubx64.efi
df /dev/nvme0n1p1
mv /mnt/boot-sav/nvme0n1p5/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p5/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p5/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p5/boot/efi/EFI/Boot/bootx64.efi
df /dev/sdb1
mv /media/ubuntu/ESD-USB/efi/Boot/bootx64.efi /media/ubuntu/ESD-USB/efi/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p5/boot/efi/efi/ubuntu/grubx64.efi /media/ubuntu/ESD-USB/efi/Boot/bootx64.efi

chroot /mnt/boot-sav/nvme0n1p5 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme0n1p5 efibootmgr -v after grub install
EFI variables are not supported on this system.

Error: NVram is locked (Ubuntu not found in efibootmgr). Veuillez indiquer ce message à boot.repair@gmail.com

chroot /mnt/boot-sav/nvme0n1p5 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-87-generic
Found initrd image: /boot/initrd.img-5.15.0-87-generic
Found linux image: /boot/vmlinuz-5.15.0-86-generic
Found initrd image: /boot/initrd.img-5.15.0-86-generic
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi

Unhide GRUB boot menu in nvme0n1p5/boot/grub/grub.cfg

Une erreur est survenue pendant la réparation.
Error: NVram is locked (Ubuntu not found in efibootmgr). Veuillez indiquer ce message à boot.repair@gmail.com

Locked-NVram détecté.


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdb.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/refind/refind.conf /efi/Boot/bkpbootx64.efi 
                       /efi/Boot/bootx64.efi /efi/refind/refind_aa64.efi 
                       /efi/refind/refind_ia32.efi /efi/refind/refind_x64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/refind/drivers_aa64/btrfs_aa64.efi 
                       /efi/refind/drivers_aa64/ext2_aa64.efi 
                       /efi/refind/drivers_aa64/ext4_aa64.efi 
                       /efi/refind/drivers_aa64/hfs_aa64.efi 
                       /efi/refind/drivers_aa64/iso9660_aa64.efi 
                       /efi/refind/drivers_aa64/reiserfs_aa64.efi 
                       /efi/refind/drivers_ia32/btrfs_ia32.efi 
                       /efi/refind/drivers_ia32/ext2_ia32.efi 
                       /efi/refind/drivers_ia32/ext4_ia32.efi 
                       /efi/refind/drivers_ia32/hfs_ia32.efi 
                       /efi/refind/drivers_ia32/iso9660_ia32.efi 
                       /efi/refind/drivers_ia32/reiserfs_ia32.efi 
                       /efi/refind/drivers_x64/btrfs_x64.efi 
                       /efi/refind/drivers_x64/ext2_x64.efi 
                       /efi/refind/drivers_x64/ext4_x64.efi 
                       /efi/refind/drivers_x64/hfs_x64.efi 
                       /efi/refind/drivers_x64/iso9660_x64.efi 
                       /efi/refind/drivers_x64/reiserfs_x64.efi 
                       /efi/refind/tools_ia32/gptsync_ia32.efi 
                       /efi/refind/tools_x64/gptsync_x64.efi

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p5: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
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
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/boot/bkpbootx64.efi /efi/boot/bootx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/microsoft/boot/cdboot.efi 
                       /efi/microsoft/boot/cdboot_noprompt.efi /bootmgr 
                       /boot/bcd


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on nvme0n1p5
OS#2:   Windows 10 or 11 on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: TU106 [GeForce RTX 2070 Rev. A] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1105(11.5) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* Windows Boot Manager    HD(1,GPT,b08ed521-de32-4162-8a04-d0f4cfea7f40,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* UEFI: General UDisk 5.00, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,MBR,0x88ddb84,0x800,0x1d4b800)..BO

a1da253696a304dce6b4668b70151c0e   nvme0n1p1/Boot/bkpbootx64.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/Boot/bootx64.efi
bac0ddd25beb4f5a8bd999d295dd63ab   nvme0n1p1/refind/refind_aa64.efi
71c7459d1db121880a1169de0f09d734   nvme0n1p1/refind/refind_ia32.efi
58375588106305df542be203d3c56cee   nvme0n1p1/refind/refind_x64.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/ubuntu/grubx64.efi
05fd7027486c73232752c9faeb99fdfe   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
87fa2cd44bed8bf4925e0045932cf67e   nvme0n1p1/Microsoft/Boot/bootmgr.efi
0ff90539cb207baf3b1e066237e4a509   nvme0n1p1/refind/drivers_aa64/btrfs_aa64.efi
aadfef4c8fe9c6180650fff8e13eb157   nvme0n1p1/refind/drivers_aa64/ext2_aa64.efi
e0a258d89d54add08d0163fc149855b2   nvme0n1p1/refind/drivers_aa64/ext4_aa64.efi
4fca55bebb229615ecce9c69540a2708   nvme0n1p1/refind/drivers_aa64/hfs_aa64.efi
7225c110aad1dec0cecbe59306578b2e   nvme0n1p1/refind/drivers_aa64/iso9660_aa64.efi
2b601db3a04812de4a6314a74e5f60b2   nvme0n1p1/refind/drivers_aa64/reiserfs_aa64.efi
96aac7e5530249060ad6a05009f18f25   nvme0n1p1/refind/drivers_ia32/btrfs_ia32.efi
810b910a08aa3eaa764e01dbb770d044   nvme0n1p1/refind/drivers_ia32/ext2_ia32.efi
e417c2e736137c8c130a3ddd175a7796   nvme0n1p1/refind/drivers_ia32/ext4_ia32.efi
fcbffa2cf6c899d318f48e9a64fcd319   nvme0n1p1/refind/drivers_ia32/hfs_ia32.efi
cdeab463506bc186f12b010be152201d   nvme0n1p1/refind/drivers_ia32/iso9660_ia32.efi
047ddf6ed0a0e73b958d0932d3489035   nvme0n1p1/refind/drivers_ia32/reiserfs_ia32.efi
6a0368185ee6de408f2d6287b7e99d2d   nvme0n1p1/refind/drivers_x64/btrfs_x64.efi
0cfc33a01c53562f7f58e91d59cc7cb2   nvme0n1p1/refind/drivers_x64/ext2_x64.efi
76636d960c2132d9fa597ffa5a04d604   nvme0n1p1/refind/drivers_x64/ext4_x64.efi
2538d0c018b6a984ca8e36f510b36ba3   nvme0n1p1/refind/drivers_x64/hfs_x64.efi
ee71e57d50cf8727004788cade1c4130   nvme0n1p1/refind/drivers_x64/iso9660_x64.efi
7941b83f26b7d77aa517f58fd6592c22   nvme0n1p1/refind/drivers_x64/reiserfs_x64.efi
bad06cf17bead8513350e016eb660042   nvme0n1p1/refind/tools_ia32/gptsync_ia32.efi
3ad8696bbc90643132457638c5b8151a   nvme0n1p1/refind/tools_x64/gptsync_x64.efi
19cb825a89130540289671cfa7fcb7c9   sdb1/boot/bkpbootx64.efi
a1da253696a304dce6b4668b70151c0e   sdb1/boot/bootx64.efi
a1da253696a304dce6b4668b70151c0e   sdb1/ubuntu/grubx64.efi
8dc6d27e97c5a894f06f9c8026e1ebc7   sdb1/microsoft/boot/cdboot.efi
5f6ec23c8bdc180a939952339be18dff   sdb1/microsoft/boot/cdboot_noprompt.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p5    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 447.13 GiB, 480103981056 bytes, 937703088 sectors
Disk identifier: 2425E326-2947-6490-3B6E-A1D34C5EA1A0
              Start       End   Sectors   Size Type
nvme0n1p1      2048    206847    204800   100M EFI System
nvme0n1p2    206848    239615     32768    16M Microsoft reserved
nvme0n1p3    239616 511004001 510764386 243.6G Microsoft basic data
nvme0n1p4 511004672 512075775   1071104   523M Windows recovery environment
nvme0n1p5 512077824 937701375 425623552   203G Microsoft basic data
Disk sda: 14.65 GiB, 15728640000 bytes, 30720000 sectors
Disk identifier: 0x088ddb84
      Boot Start      End  Sectors  Size Id Type
sda1  *     2048 30719999 30717952 14.6G  c W95 FAT32 (LBA)
Disk sdb: 14.65 GiB, 15728640000 bytes, 30720000 sectors
Disk identifier: 0x8a3c730f
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 30719999 30717952 14.6G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:15.7GB:scsi:512:512:msdos:General UDisk:;
1:1049kB:15.7GB:15.7GB:fat32::boot, lba;
sdb:15.7GB:scsi:512:512:msdos:General UDisk:;
1:1049kB:15.7GB:15.7GB:fat32::boot, lba;
nvme0n1:480GB:nvme:512:512:gpt:Force MP510:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:262GB:262GB:ntfs:Basic data partition:msftdata;
4:262GB:262GB:548MB:ntfs::hidden, diag;
5:262GB:480GB:218GB:ext4::msftdata;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9492;&#9472;sda1      vfat     3C23-682F                            088ddb84-01                          UBUNTU 22_0 
sdb                                                                                                        
&#9492;&#9472;sdb1      vfat     46D7-C0BE                            8a3c730f-01                          ESD-USB     
nvme0n1                                                                                                    
&#9500;&#9472;nvme0n1p1 vfat     CA32-EC71                            b08ed521-de32-4162-8a04-d0f4cfea7f40             EFI system partition
&#9500;&#9472;nvme0n1p2                                               303898e9-4fa2-488d-a243-5deeb0aebc2c             Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     10E43645E4362D7A                     11b8ebd2-db9e-45ae-a402-d08af272195e             Basic data partition
&#9500;&#9472;nvme0n1p4 ntfs     B0003E95003E6290                     0557839f-7b33-41c9-b7fe-5f3e8266acfd             
&#9492;&#9472;nvme0n1p5 ext4     ea051475-6895-4b71-81a0-74e83cd6f2c0 10d17a84-fcba-c925-aff8-dfd138c296b4             

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/nvme0n1p1             61.4M  36% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3            184.7G  24% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4             88.7M  83% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5               11G  89% /mnt/boot-sav/nvme0n1p5
/dev/sda1                   9.9G  32% /cdrom
/dev/sdb1                  10.1G  31% /media/ubuntu/ESD-USB

Mount options (filtered): ______________________________________________________


================= nvme0n1p1/EFI/refind/refind.conf (filtered) ==================

timeout 20
use_nvram false
menuentry Linux {
    icon EFI/refind/icons/os_linux.png
    volume 904404F8-B481-440C-A1E3-11A5A954E601
    loader bzImage-3.3.0-rc7
    initrd initrd-3.3.0.img
    options "ro root=UUID=5f96cafa-e0a7-4057-b18f-fa709db5b837"
    disabled
}
menuentry "Arch Linux" {
    icon     /EFI/refind/icons/os_arch.png
    volume   "Arch Linux"
    loader   /boot/vmlinuz-linux
    initrd   /boot/initramfs-linux.img
    options  "root=PARTUUID=5028fa50-0079-4c40-b240-abfaf28693ea rw add_efi_memmap"
    submenuentry "Boot using fallback initramfs" {
        initrd /boot/initramfs-linux-fallback.img
    }
    submenuentry "Boot to terminal" {
        add_options "systemd.unit=multi-user.target"
    }
    disabled
}
menuentry Ubuntu {
    loader /EFI/ubuntu/grubx64.efi
    icon /EFI/refind/icons/os_linux.png
    disabled
}
menuentry "ELILO" {
    loader \EFI\elilo\elilo.efi
    disabled
}
menuentry "Windows 7" {
    loader \EFI\Microsoft\Boot\bootmgfw.efi
    disabled
}
menuentry "Windows via shell script" {
    icon \EFI\refind\icons\os_win.png
    loader \EFI\tools\shell.efi
    options "fs0:\EFI\tools\launch_windows.nsh"
    disabled
}
menuentry "My macOS" {
    icon \EFI\refind\icons\os_mac.png
    volume "macOS boot"
    loader \System\Library\CoreServices\boot.efi
    disabled
}
menuentry "macOS via BootNext" {
    icon /EFI/refind/icons/os_mac.png
    firmware_bootnum 80
    disabled
}

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid ea051475-6895-4b71-81a0-74e83cd6f2c0 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p5/boot/grub/grub.cfg (filtered) ====================

Ubuntu   ea051475-6895-4b71-81a0-74e83cd6f2c0
Ubuntu, with Linux 5.15.0-87-generic   ea051475-6895-4b71-81a0-74e83cd6f2c0
Ubuntu, with Linux 5.15.0-86-generic   ea051475-6895-4b71-81a0-74e83cd6f2c0
Windows Boot Manager (on nvme0n1p1)   osprober-efi-CA32-EC71
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p5/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=ea051475-6895-4b71-81a0-74e83cd6f2c0 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
UUID=CA32-EC71  /boot/efi       vfat    defaults      0       1

==================== nvme0n1p5/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p5: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 272,035842896 = 292,096262144  boot/vmlinuz                                  11
 445,918331146 = 478,801162240  boot/vmlinuz-5.15.0-86-generic                20
 272,035842896 = 292,096262144  boot/vmlinuz-5.15.0-87-generic                11
 445,918331146 = 478,801162240  boot/vmlinuz.old                              20
 346,083263397 = 371,604074496  boot/initrd.img                               70
 422,358112335 = 453,503569920  boot/initrd.img-5.15.0-86-generic             78
 346,083263397 = 371,604074496  boot/initrd.img-5.15.0-87-generic             70
 422,358112335 = 453,503569920  boot/initrd.img.old                           78

=================== nvme0n1p5: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

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
```

And this the boot info :

```

boot-info-4ppa2056                                              [20231029_1011]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/refind/refind.conf /efi/Boot/bkpbootx64.efi 
                       /efi/Boot/bootx64.efi /efi/refind/refind_aa64.efi 
                       /efi/refind/refind_ia32.efi /efi/refind/refind_x64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/refind/drivers_aa64/btrfs_aa64.efi 
                       /efi/refind/drivers_aa64/ext2_aa64.efi 
                       /efi/refind/drivers_aa64/ext4_aa64.efi 
                       /efi/refind/drivers_aa64/hfs_aa64.efi 
                       /efi/refind/drivers_aa64/iso9660_aa64.efi 
                       /efi/refind/drivers_aa64/reiserfs_aa64.efi 
                       /efi/refind/drivers_ia32/btrfs_ia32.efi 
                       /efi/refind/drivers_ia32/ext2_ia32.efi 
                       /efi/refind/drivers_ia32/ext4_ia32.efi 
                       /efi/refind/drivers_ia32/hfs_ia32.efi 
                       /efi/refind/drivers_ia32/iso9660_ia32.efi 
                       /efi/refind/drivers_ia32/reiserfs_ia32.efi 
                       /efi/refind/drivers_x64/btrfs_x64.efi 
                       /efi/refind/drivers_x64/ext2_x64.efi 
                       /efi/refind/drivers_x64/ext4_x64.efi 
                       /efi/refind/drivers_x64/hfs_x64.efi 
                       /efi/refind/drivers_x64/iso9660_x64.efi 
                       /efi/refind/drivers_x64/reiserfs_x64.efi 
                       /efi/refind/tools_ia32/gptsync_ia32.efi 
                       /efi/refind/tools_x64/gptsync_x64.efi

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p5: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on nvme0n1p5
OS#2:   Windows 10 or 11 on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: TU106 [GeForce RTX 2070 Rev. A] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1105(11.5) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* Windows Boot Manager    HD(1,GPT,b08ed521-de32-4162-8a04-d0f4cfea7f40,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* UEFI: General UDisk 5.00, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(1,MBR,0x88ddb84,0x800,0x1d4b800)..BO

a1da253696a304dce6b4668b70151c0e   nvme0n1p1/Boot/bkpbootx64.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/Boot/bootx64.efi
bac0ddd25beb4f5a8bd999d295dd63ab   nvme0n1p1/refind/refind_aa64.efi
71c7459d1db121880a1169de0f09d734   nvme0n1p1/refind/refind_ia32.efi
58375588106305df542be203d3c56cee   nvme0n1p1/refind/refind_x64.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/ubuntu/grubx64.efi
05fd7027486c73232752c9faeb99fdfe   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
87fa2cd44bed8bf4925e0045932cf67e   nvme0n1p1/Microsoft/Boot/bootmgr.efi
0ff90539cb207baf3b1e066237e4a509   nvme0n1p1/refind/drivers_aa64/btrfs_aa64.efi
aadfef4c8fe9c6180650fff8e13eb157   nvme0n1p1/refind/drivers_aa64/ext2_aa64.efi
e0a258d89d54add08d0163fc149855b2   nvme0n1p1/refind/drivers_aa64/ext4_aa64.efi
4fca55bebb229615ecce9c69540a2708   nvme0n1p1/refind/drivers_aa64/hfs_aa64.efi
7225c110aad1dec0cecbe59306578b2e   nvme0n1p1/refind/drivers_aa64/iso9660_aa64.efi
2b601db3a04812de4a6314a74e5f60b2   nvme0n1p1/refind/drivers_aa64/reiserfs_aa64.efi
96aac7e5530249060ad6a05009f18f25   nvme0n1p1/refind/drivers_ia32/btrfs_ia32.efi
810b910a08aa3eaa764e01dbb770d044   nvme0n1p1/refind/drivers_ia32/ext2_ia32.efi
e417c2e736137c8c130a3ddd175a7796   nvme0n1p1/refind/drivers_ia32/ext4_ia32.efi
fcbffa2cf6c899d318f48e9a64fcd319   nvme0n1p1/refind/drivers_ia32/hfs_ia32.efi
cdeab463506bc186f12b010be152201d   nvme0n1p1/refind/drivers_ia32/iso9660_ia32.efi
047ddf6ed0a0e73b958d0932d3489035   nvme0n1p1/refind/drivers_ia32/reiserfs_ia32.efi
6a0368185ee6de408f2d6287b7e99d2d   nvme0n1p1/refind/drivers_x64/btrfs_x64.efi
0cfc33a01c53562f7f58e91d59cc7cb2   nvme0n1p1/refind/drivers_x64/ext2_x64.efi
76636d960c2132d9fa597ffa5a04d604   nvme0n1p1/refind/drivers_x64/ext4_x64.efi
2538d0c018b6a984ca8e36f510b36ba3   nvme0n1p1/refind/drivers_x64/hfs_x64.efi
ee71e57d50cf8727004788cade1c4130   nvme0n1p1/refind/drivers_x64/iso9660_x64.efi
7941b83f26b7d77aa517f58fd6592c22   nvme0n1p1/refind/drivers_x64/reiserfs_x64.efi
bad06cf17bead8513350e016eb660042   nvme0n1p1/refind/tools_ia32/gptsync_ia32.efi
3ad8696bbc90643132457638c5b8151a   nvme0n1p1/refind/tools_x64/gptsync_x64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p5    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 447.13 GiB, 480103981056 bytes, 937703088 sectors
Disk identifier: 2425E326-2947-6490-3B6E-A1D34C5EA1A0
              Start       End   Sectors   Size Type
nvme0n1p1      2048    206847    204800   100M EFI System
nvme0n1p2    206848    239615     32768    16M Microsoft reserved
nvme0n1p3    239616 511004001 510764386 243.6G Microsoft basic data
nvme0n1p4 511004672 512075775   1071104   523M Windows recovery environment
nvme0n1p5 512077824 937701375 425623552   203G Microsoft basic data
Disk sda: 14.65 GiB, 15728640000 bytes, 30720000 sectors
Disk identifier: 0x088ddb84
      Boot Start      End  Sectors  Size Id Type
sda1  *     2048 30719999 30717952 14.6G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:15.7GB:scsi:512:512:msdos:General UDisk:;
1:1049kB:15.7GB:15.7GB:fat32::boot, lba;
nvme0n1:480GB:nvme:512:512:gpt:Force MP510:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:262GB:262GB:ntfs:Basic data partition:msftdata;
4:262GB:262GB:548MB:ntfs::hidden, diag;
5:262GB:480GB:218GB:ext4::msftdata;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9492;&#9472;sda1      vfat     3C23-682F                            088ddb84-01                          UBUNTU 22_0 
nvme0n1                                                                                                    
&#9500;&#9472;nvme0n1p1 vfat     CA32-EC71                            b08ed521-de32-4162-8a04-d0f4cfea7f40             EFI system partition
&#9500;&#9472;nvme0n1p2                                               303898e9-4fa2-488d-a243-5deeb0aebc2c             Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     10E43645E4362D7A                     11b8ebd2-db9e-45ae-a402-d08af272195e             Basic data partition
&#9500;&#9472;nvme0n1p4 ntfs     B0003E95003E6290                     0557839f-7b33-41c9-b7fe-5f3e8266acfd             
&#9492;&#9472;nvme0n1p5 ext4     ea051475-6895-4b71-81a0-74e83cd6f2c0 10d17a84-fcba-c925-aff8-dfd138c296b4             

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/nvme0n1p1             61.4M  36% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3            184.7G  24% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4             88.7M  83% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5               11G  89% /mnt/boot-sav/nvme0n1p5
/dev/sda1                   9.9G  32% /cdrom

Mount options (filtered): ______________________________________________________


================= nvme0n1p1/EFI/refind/refind.conf (filtered) ==================

timeout 20
use_nvram false
menuentry Linux {
    icon EFI/refind/icons/os_linux.png
    volume 904404F8-B481-440C-A1E3-11A5A954E601
    loader bzImage-3.3.0-rc7
    initrd initrd-3.3.0.img
    options "ro root=UUID=5f96cafa-e0a7-4057-b18f-fa709db5b837"
    disabled
}
menuentry "Arch Linux" {
    icon     /EFI/refind/icons/os_arch.png
    volume   "Arch Linux"
    loader   /boot/vmlinuz-linux
    initrd   /boot/initramfs-linux.img
    options  "root=PARTUUID=5028fa50-0079-4c40-b240-abfaf28693ea rw add_efi_memmap"
    submenuentry "Boot using fallback initramfs" {
        initrd /boot/initramfs-linux-fallback.img
    }
    submenuentry "Boot to terminal" {
        add_options "systemd.unit=multi-user.target"
    }
    disabled
}
menuentry Ubuntu {
    loader /EFI/ubuntu/grubx64.efi
    icon /EFI/refind/icons/os_linux.png
    disabled
}
menuentry "ELILO" {
    loader \EFI\elilo\elilo.efi
    disabled
}
menuentry "Windows 7" {
    loader \EFI\Microsoft\Boot\bootmgfw.efi
    disabled
}
menuentry "Windows via shell script" {
    icon \EFI\refind\icons\os_win.png
    loader \EFI\tools\shell.efi
    options "fs0:\EFI\tools\launch_windows.nsh"
    disabled
}
menuentry "My macOS" {
    icon \EFI\refind\icons\os_mac.png
    volume "macOS boot"
    loader \System\Library\CoreServices\boot.efi
    disabled
}
menuentry "macOS via BootNext" {
    icon /EFI/refind/icons/os_mac.png
    firmware_bootnum 80
    disabled
}

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid ea051475-6895-4b71-81a0-74e83cd6f2c0 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p5/boot/grub/grub.cfg (filtered) ====================

Ubuntu   ea051475-6895-4b71-81a0-74e83cd6f2c0
Ubuntu, with Linux 5.15.0-87-generic   ea051475-6895-4b71-81a0-74e83cd6f2c0
Ubuntu, with Linux 5.15.0-86-generic   ea051475-6895-4b71-81a0-74e83cd6f2c0
Windows Boot Manager (on nvme0n1p1)   osprober-efi-CA32-EC71
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p5/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=ea051475-6895-4b71-81a0-74e83cd6f2c0 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
UUID=CA32-EC71  /boot/efi       vfat    defaults      0       1

==================== nvme0n1p5/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p5: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 312,309085846 = 335,339327488  boot/grub/grub.cfg                             1
 272,035842896 = 292,096262144  boot/vmlinuz                                  11
 445,918331146 = 478,801162240  boot/vmlinuz-5.15.0-86-generic                20
 272,035842896 = 292,096262144  boot/vmlinuz-5.15.0-87-generic                11
 445,918331146 = 478,801162240  boot/vmlinuz.old                              20
 346,083263397 = 371,604074496  boot/initrd.img                               70
 422,358112335 = 453,503569920  boot/initrd.img-5.15.0-86-generic             78
 346,083263397 = 371,604074496  boot/initrd.img-5.15.0-87-generic             70
 422,358112335 = 453,503569920  boot/initrd.img.old                           78

=================== nvme0n1p5: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

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



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p5,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)

```



I know this topic is common but I haven't found a solution adapted to my problem.

Could someone help me find my dual boot please?

Thank you so much !

---

### Post by james64000 on 2023-10-29
It's OK with : [https://www.supergrubdisk.org/wizard-restore-grub-with-super-grub2-disk/](https://www.supergrubdisk.org/wizard-restore-grub-with-super-grub2-disk/)

---

### Post by yancek on 2023-10-29
Can you boot windows?  Have you disabled Secure Boot and BitLocker?  I've seen several posts recently about the nvram being locked but don't know the solution.

---

