---
title: "boot issues"
date: 2024-09-18
forum: Installation &amp; Upgrades
---

### Post by patelbrijes on 2024-09-18
trying to install ubuntu 24.04 LTS from USB ISO image and cannot detect the bootable device after restart.

any help will be much appreciated

ran the boot repair and the summary is as follows:

Boot summary info: [https://paste.ubuntu.com/p/n3YVFfWZnz/](https://paste.ubuntu.com/p/n3YVFfWZnz/)

Boot repair: [https://paste.ubuntu.com/p/hK4xdQvWBJ/](https://paste.ubuntu.com/p/hK4xdQvWBJ/)

boot-repair-4ppa2081                                              [20240918_1416]


```
============================== Boot Info Summary ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------


sda1: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi




================================ 1 OS detected =================================


OS#1 (linux):   Ubuntu 24.04.1 LTS on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Atom Processor Z36xxx/Z37xxx Series Graphics & Display from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 24.04.1 LTS, noble, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: FYBYT10H.86A.0040.2014.0923.1932(5.6) from Intel Corp.
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).






============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda2    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB


Partitions info (2/3): _________________________________________________________


sda2    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4


Partitions info (3/3): _________________________________________________________


sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 5A701D16-D137-4AC5-AF71-07DC0925F34D
     Start       End   Sectors   Size Type
sda1   2048      4095      2048     1M BIOS boot
sda2   4096 976771071 976766976 465.8G Linux filesystem
Disk sdb: 58.59 GiB, 62914560000 bytes, 122880000 sectors
Disk identifier: 0x173d9ae0
     Boot Start       End   Sectors  Size Id Type
sdb1  *     2048 122879935 122877888 58.6G  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:500GB:scsi:512:4096:gpt:ATA WDC WD5000LPVX-8:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:500GB:500GB:ext4::;
sdb:62.9GB:scsi:512:512:msdos: USB DISK 3.0:;
1:1049kB:62.9GB:62.9GB:fat32::boot, lba;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1                                               c248ed46-7383-4d37-86df-8afd6aab419a             
&#9492;&#9472;sda2 ext4     5e64bbd9-ad4b-49c2-ba68-3cc8d6625209 2430e5ca-897d-4895-a51a-10fdec40aaf7             
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     1F1E-2D61                            173d9ae0-01                          UBUNTU 24_0 


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda2              425.6G   2% /mnt/boot-sav/sda2
/dev/sdb1               52.8G  10% /cdrom


Mount options (filtered): ______________________________________________________


/dev/sda2              ext4            rw,relatime
/dev/sdb1              vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro


====================== sda2/boot/grub/grub.cfg (filtered) ======================


Ubuntu   5e64bbd9-ad4b-49c2-ba68-3cc8d6625209
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda2/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/5e64bbd9-ad4b-49c2-ba68-3cc8d6625209 / ext4 defaults 0 1
/swap.img    none    swap    sw    0    0


======================= sda2/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


==================== sda2: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 146.303134918 = 157.091794944  boot/grub/grub.cfg                             1
 296.603321075 = 318.475390976  boot/grub/i386-pc/core.img                     1
 292.875247955 = 314.472402944  boot/vmlinuz                                   1
 292.875247955 = 314.472402944  boot/vmlinuz-6.8.0-45-generic                  1
 292.875247955 = 314.472402944  boot/vmlinuz.old                               1
 296.672496796 = 318.549667840  boot/initrd.img                                2
 296.672496796 = 318.549667840  boot/initrd.img-6.8.0-45-generic               2
 296.672496796 = 318.549667840  boot/initrd.img.old                            2


===================== sda2: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 10:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5 11:36 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4 10:12 40_custom
-rwxr-xr-x 1 root root   215 Apr  4 10:12 41_custom


====================== sdb1/boot/grub/grub.cfg (filtered) ======================


Try or Install Ubuntu
Ubuntu (safe graphics)
Boot from next volume
UEFI Firmware Settings
Test memory


==================== sdb1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub2 of
sda2 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s


Final advice in case of suggested repair: ______________________________________




The boot files of [sda2 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
```

---

### Post by oldfred on 2024-09-18
Please use Code tags with text or terminal output. Uses fixed font for better readability.
Code Tags
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

You show newer UEFI system but have older BIOS boot.
Drive is gpt and has required bios_grub partition for BIOS boot on gpt. But has no ESP - efi system partition for UEFI boot.

You may just need to change UEFI boot settings from UEFI to BIOS/Legacy/CSM or whatever your system calls it.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

If you want to convert to UEFI install, you just need to add an ESP, FAT32 with boot,esp flags & reinstall grub. Or do total reinstall by booting installer in UEFI boot mode.

How you boot install media UEFI or BIOS, is then how it installs.
But UEFI settings may be set for one or the other. Some will boot either mode without changing settings, but varies by UEFI vendor.

---

