---
title: "No dual install of Ubuntu 18.04 with Windows 8.1"
date: 2018-10-18
forum: Installation &amp; Upgrades
---

### Post by willem-v on 2018-10-18
After I put a problem here - I got no Internet en email on my Ubunto 18.04 - there was no satisfying answer. In this case I installed a new 18.04 on my computer. It was een dual OS because I've also Windows there for some other things. I first "Try Ubuntu" of the internet works and .. yes! So, I pressed to install Ubuntu and 'everything'(*1) was going well, till I wanna boot. During this process a message came from Ubuntu : "\ubuntu \winboot\wublidr.mbr" isn't there or is corrupted. Okay, I'll look into some archives, my PC is a Windows 8.1 and I want a Ubuntu 18.04 installed. For example this one : [https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi) . In this case, the Secure Boot is disabled, the command : 'bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi' is set, Fast StartUp from Windows disabled, boot-repair(*2) called in, etc. But, still nothing there. No boot. At the end my question is, Wubi uses MBR to boot Ubuntu installed in Windows partition. When Windows boots using UEFI, the MBR does not work and thus users will not be able to boot into Ubuntu. See : [https://bugs.launchpad.net/wubi/+bug/694242](https://bugs.launchpad.net/wubi/+bug/694242). My Windows uses EFI and  - a long time ago - it was a Wubi who installed an Ubuntu 14.04 on my PC.

There are some issues :
(*1) When I pressed under which OS I choose in Ubuntu "Something else" and  after that "Install Now" I'll get the message : "No root file system is defined. Please correct this from te partitioning menu". Do they think that I partioned it?? Btw, I'll have to go "Back" to the OS choice before.
(*2) message : "The filebrowser that you just opened will let you access your Wubi (Linux installed into Window files /mnt/boot-sav/wub1/home). Please backup your data now!"

---

### Post by yancek on 2018-10-18
The Ubuntu Wubi Guide at the link below explains that wubi is not and has not been supported for several years and definitely is not expected to work with window 8/10.  For that reason, you will not likely get much help at these forums.  If you don't want to install Ubuntu directly on your hardware you can try using virtual software, VirtualBox, VMWare or similar.

 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> No root file system is defined. Please correct this from te partitioning menu".

You need to select a previously created partition or unallocated space on a drive and then select a Mount Point when you are using the Something Else Installation type option if you are installing directly.  
Wubi created a menu entry in the windows bootloader to boot the Ubuntu and that won't work with an EFI install.

---

### Post by willem-v on 2018-10-20
I've made some progress. Wubi is terminated on my PC and new installation is formed. The error of \ubuntu\winboot\wublidr.mbr is gone. In the system 
there are 3 boots relevant :

1. USB Key:EUFI USB Disk: 2.0 PMAP                        
2. Hard Disk : Ubuntu (PO: WDC WD5OOOAAKX-OOERMAO)             | ===> Boot loader : /dev/sda ATA WDC WD5OOOAAKX-O)
3. Windows Boot Manager (PO: WDC WD5OOOAAKX-OOERMAO)       |

/dev/sda2 : EFI from Windows 
/dev/sda7 : Ubuntu
/dev/sda8 : swap

With (1) I'll get to install an Ubuntu on my PC :

_____________________________________________________________

a. Try Ubuntu without installing
b. Install Ubuntu
c. OEM install (for manufactures)
d. Check disk for defects

Number (1a) works fine. I've made a boot-repair, the grub-efi-amd64-signed and linux-generic must be incorperated. I've done that. But when I wanna 
restart it, the computer comes back with the list of 4. Again I'll made boot-repair the PC asked again for the 2 things above...

When press on "Something else" and install, a message appear : "No root file system is defined. Please correct this from the partitioning menu". I've 
read about this, but  putting (/) there and install Ubuntu, a person adressed : "Although, as your Windows is installed in UEFI mode you can experience 
problems, such as booting straight to Windows and not passing through GRUB", so I don't wanna do it. I'll need my Windows for now, for example to pay 
my debts. 

Number (1b) haven the same result. 

Number (1d) are 2 mismatchs :

- /boot/grup/grup.cfg
- /boot/grup/loopback.cfg

____________________________________________________________

Number (2) :

- grup>

This a minimal bash. Bootloader doesn't work. With a TAB you will get the options. With an ESC you will go to Windows.

___________________________________________________________

Number (3) :

Okay. Boot loader of Windows 8.1 works.

#######################################

Any recommendations?

---

### Post by oldfred on 2018-10-20
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by willem-v on 2018-10-20
You can find it  :

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1798970](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1798970)

---

### Post by oldfred on 2018-10-20
Bug report does not help.
Need to see Summary Report from Boot-Repair.
And what brand/model system?
What video card/chip?

---

### Post by willem-v on 2018-10-20
```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdb.

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
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/Boot/bootx64.efi 
                       /EFI/Boot/fbx64.efi /EFI/ubuntu/fwupx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda3: unknown filesystem type ''.

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/boot/bootx64.efi /boot/bcd

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.1 LTS
    Boot files:        /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 8512 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,023,999     1,021,952 Windows Recovery Environment (Windows)
/dev/sda2             1,024,000     1,228,799       204,800 EFI System partition
/dev/sda3             1,228,800     1,490,943       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4      R      1,490,944     3,588,095     2,097,152 -
/dev/sda5             3,588,096   247,946,217   244,358,122 Data partition (Windows/Linux)
/dev/sda6           850,946,048   976,762,879   125,816,832 Data partition (Windows/Linux)
/dev/sda7           247,947,264   842,723,327   594,776,064 Data partition (Linux)
/dev/sda8           842,723,328   850,946,047     8,222,720 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 14.5 GiB, 15513354240 bytes, 30299520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    30,299,519    30,291,456   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/sda1        E0888C54888C2B5C                       ntfs       
/dev/sda2        7A8C-9328                              vfat       
/dev/sda3                                                          
/dev/sda4        0466-BB64                              vfat       PRC_RP
/dev/sda5        3E528BB6528B7207                       ntfs       Boot
/dev/sda6        8896BA5696BA450A                       ntfs       Recover
/dev/sda7        82be5947-9bc4-4991-bdba-c73f872bc3ff   ext4       
/dev/sda8        7eef6ae6-eea7-4be3-a81d-ef21b16ad510   swap       
/dev/sdb1        9F58-46A8                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct 20 18:36 ata-TSSTcorp_CDDVDW_SH-216DB_R96V68EF200645 -> ../../sr0
lrwxrwxrwx 1 root root  9 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Oct 20 18:42 ata-WDC_WD5000AAKX-00ERMA0_WD-WCC2E1FZH7FU-part8 -> ../../sda8
lrwxrwxrwx 1 root root  9 Oct 20 18:42 usb-_USB_DISK_2.0_0708447D951B6397-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 20 18:42 usb-_USB_DISK_2.0_0708447D951B6397-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Oct 20 18:42 wwn-0x50014ee2609db112 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 20 18:42 wwn-0x50014ee2609db112-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 20 18:42 wwn-0x50014ee2609db112-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 20 18:42 wwn-0x50014ee2609db112-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 20 18:42 wwn-0x50014ee2609db112-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Oct 20 18:42 wwn-0x50014ee2609db112-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 20 18:42 wwn-0x50014ee2609db112-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Oct 20 18:42 wwn-0x50014ee2609db112-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Oct 20 18:42 wwn-0x50014ee2609db112-part8 -> ../../sda8

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda2/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid df91df17-bce9-416e-b4f4-b1ff9a229e1c root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=82be5947-9bc4-4991-bdba-c73f872bc3ff /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=7A8C-9328  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 378.463607788 = 406.372204544  boot/vmlinuz-4.15.0-29-generic                 1
 378.469520569 = 406.378553344  boot/vmlinuz-4.15.0-29-generic.efi.signed      1
 378.463607788 = 406.372204544  vmlinuz                                        1
 378.463607788 = 406.372204544  vmlinuz.old                                    1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

set timeout=5
menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
c60c7f8d9e87f647a7670ed8fd3b0659

=============================== StdErr Messages: ===============================

File descriptor 63 (pipe:[80594]) leaked on lvs invocation. Parent PID 32288: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 20181020_1842 ===================
boot-info version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-info is executed in live-session (Ubuntu 18.04.1 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:
/dev/sda2@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sda7:Ubuntu 18.04.1 LTS (18.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="E0888C54888C2B5C" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="97dbbad5-1341-11e4-827e-d43d7e6c632f"
/dev/sda2: UUID="7A8C-9328" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="97dbbad6-1341-11e4-827e-d43d7e6c632f"
/dev/sda4: LABEL="PRC_RP" UUID="0466-BB64" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="97dbbad8-1341-11e4-827e-d43d7e6c632f"
/dev/sda5: LABEL="Boot" UUID="3E528BB6528B7207" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="97dbbad9-1341-11e4-827e-d43d7e6c632f"
/dev/sda6: LABEL="Recover" UUID="8896BA5696BA450A" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="aa7b6a77-6f0c-4b64-9cc5-e2c209505c82"
/dev/sda7: UUID="82be5947-9bc4-4991-bdba-c73f872bc3ff" TYPE="ext4" PARTUUID="0c46476d-da5b-4816-abd1-2b30afb69f77"
/dev/sdb1: LABEL="UUI" UUID="9F58-46A8" TYPE="vfat" PARTUUID="9e04baec-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda8: UUID="7eef6ae6-eea7-4be3-a81d-ef21b16ad510" TYPE="swap" PARTUUID="4c433ce9-43d2-4055-815c-16a005777a75"
/dev/sda3: PARTLABEL="Microsoft reserved partition" PARTUUID="97dbbad7-1341-11e4-827e-d43d7e6c632f"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda5.
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/fbx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda4/EFI/Boot/bootx64.efi

=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 25 03:08 grub.d
total 80
-rwxr-xr-x 1 root root  9783 Jul 17 18:13 00_header
-rwxr-xr-x 1 root root  6258 Jul 16 15:15 05_debian_theme
-rwxr-xr-x 1 root root 12693 Jul 17 18:13 10_linux
-rwxr-xr-x 1 root root 11298 Jul 17 18:13 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Jul 17 18:13 30_os-prober
-rwxr-xr-x 1 root root  1418 Jul 17 18:13 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jul 17 18:13 40_custom
-rwxr-xr-x 1 root root   216 Jul 17 18:13 41_custom
-rw-r--r-- 1 root root   483 Jul 17 18:13 README




=================== sda7/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== No kernel in /mnt/boot-sav/sda7/boot:
System.map-4.15.0-29-generic
abi-4.15.0-29-generic
config-4.15.0-29-generic
efi
grub
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
retpoline-4.15.0-29-generic
vmlinuz-4.15.0-29-generic
vmlinuz-4.15.0-29-generic.efi.signed


/boot/efi detected in the fstab of sda7: UUID=7A8C-9328   (sda2)
/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0005,0001,0004,0002,0003,0000
Boot0000* Windows Boot Manager    HD(2,GPT,97dbbad6-1341-11e4-827e-d43d7e6c632f,0xfa000,0x32000)/File(EFIubuntushimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...6................
Boot0001* Windows Boot Manager (P0: WDC WD5000AAKX-00ERMA0)    HD(2,GPT,97dbbad6-1341-11e4-827e-d43d7e6c632f,0xfa000,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)..BO
Boot0002* UEFI OS (P0: WDC WD5000AAKX-00ERMA0)    HD(4,GPT,97dbbad8-1341-11e4-827e-d43d7e6c632f,0x16c000,0x200000)/File(EFIBOOTBOOTX64.EFI)..BO
Boot0003* ubuntu    HD(2,GPT,97dbbad6-1341-11e4-827e-d43d7e6c632f,0xfa000,0x32000)/File(EFIUBUNTUSHIMX64.EFI)
Boot0004* ubuntu (P0: WDC WD5000AAKX-00ERMA0)    HD(2,GPT,97dbbad6-1341-11e4-827e-d43d7e6c632f,0xfa000,0x32000)/File(EFIUBUNTUGRUBX64.EFI)..BO
Boot0005* UEFI:  USB DISK 2.0 PMAP    PciRoot(0x0)/Pci(0x14,0x0)/USB(4,0)/HD(1,MBR,0x9e04baec,0x1f80,0x1ce3600)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda2.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda6.
sda7    : sda,    not-sepboot,    no-grubenv    grub2,    grub-pc ,    update-grub,    64,    no-kernel,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda7.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:gpt:ATA WDC WD5000AAKX-0:;
1:1049kB:524MB:523MB:ntfs:Basic data partition:diag;
2:524MB:629MB:105MB:fat32:EFI system partition:boot, esp;
3:629MB:763MB:134MB::Microsoft reserved partition:msftres;
4:763MB:1837MB:1074MB:fat32:Basic data partition:hidden;
5:1837MB:127GB:125GB:ntfs:Basic data partition:msftdata;
7:127GB:431GB:305GB:ext4::;
8:431GB:436GB:4210MB:linux-swap(v1)::;
6:436GB:500GB:64.4GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdb:15.5GB:scsi:512:512:msdos: USB DISK 2.0:;
1:4129kB:15.5GB:15.5GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs   1.8G
loop1 loop squashfs  86.9M
loop2 loop squashfs  34.7M
loop3 loop squashfs 140.9M
loop4 loop squashfs   2.3M
loop5 loop squashfs    13M
loop6 loop squashfs  14.5M
loop7 loop squashfs   3.7M
sda   disk          465.8G
sda1  part ntfs       499M
sda2  part vfat       100M
sda3  part            128M
sda4  part vfat         1G PRC_RP
sda5  part ntfs     116.5G Boot
sda6  part ntfs        60G Recover
sda7  part ext4     283.6G
sda8  part swap       3.9G
sdb   disk           14.5G
sdb1  part vfat      14.5G UUI
sr0   rom            1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
loop1    1  1  0         /snap/core/4917
loop2    1  1  0         /snap/gtk-common-themes/319
loop3    1  1  0         /snap/gnome-3-26-1604/70
loop4    1  1  0         /snap/gnome-calculator/180
loop5    1  1  0         /snap/gnome-characters/103
loop6    1  1  0         /snap/gnome-logs/37
loop7    1  1  0         /snap/gnome-system-monitor/51
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0
sda4     1  0  0         /mnt/boot-sav/sda4
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0         /mnt/boot-sav/sda6
sda7     1  0  0         /mnt/boot-sav/sda7
sda8     1  0  0         [SWAP]
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4021036k,nr_inodes=1005259,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=808444k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15571)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=808440k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/var/lib/snapd/snaps/core_4917.snap on /snap/core/4917 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_319.snap on /snap/gtk-common-themes/319 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_70.snap on /snap/gnome-3-26-1604/70 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_180.snap on /snap/gnome-calculator/180 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_103.snap on /snap/gnome-characters/103 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_37.snap on /snap/gnome-logs/37 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_51.snap on /snap/gnome-system-monitor/51 type squashfs (ro,nodev,relatime,x-gdu.hide)
tmpfs on /run/user/0 type tmpfs (rw,nosuid,nodev,relatime,size=808440k,mode=700)
gvfsd-fuse on /run/user/0/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=0,group_id=0)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda4 on /mnt/boot-sav/sda4 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw,relatime,data=ordered)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 initctl input kmsg kvm lightnvm log mapper mcelog mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 97 0f 00 00 00 00 00  |................|
00000030  55 a6 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U...............|
00000040  f6 00 00 00 01 00 00 00  5c 2b 8c 88 54 8c 88 e0  |........+..T...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 a0 0f 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 28 93 8c 7a 4e  4f 20 4e 41 4d 45 20 20  |..)(..zNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200
efi files in sda4/efi: /boot/bootx64.efi

=================== hexdump -n512 -C /dev/sda4
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 0e 10  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 c0 16 00  |........?.......|
00000020  00 00 20 00 f9 07 00 00  00 00 00 00 02 00 00 00  |.. .............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 64 bb 66 04 4e  4f 20 4e 41 4d 45 20 20  |..)d.f.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 c0 36 00  |........?.....6.|
00000020  00 00 00 00 80 00 80 00  e0 9b 90 0e 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  07 72 8b 52 b6 8b 52 3e  |.........r.R..R>|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 b8 32  |........?....h.2|
00000020  00 00 00 00 80 00 80 00  ff cf 7f 07 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  0a 45 ba 96 56 ba 96 88  |.........E..V...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     790M  2.1M  788M   1% /run
/dev/sdb1      vfat       15G  4.7G  9.9G  32% /cdrom
/dev/loop0     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   3.9G  410M  3.5G  11% /
tmpfs          tmpfs     3.9G   20M  3.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G  740K  3.9G   1% /tmp
tmpfs          tmpfs     790M   44K  790M   1% /run/user/999
/dev/loop1     squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop2     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop3     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop4     squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop5     squashfs   13M   13M     0 100% /snap/gnome-characters/103
/dev/loop6     squashfs   15M   15M     0 100% /snap/gnome-logs/37
/dev/loop7     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
tmpfs          tmpfs     790M  4.0K  790M   1% /run/user/0
/dev/sda1      fuseblk   499M  308M  192M  62% /mnt/boot-sav/sda1
/dev/sda2      vfat       96M   31M   66M  32% /mnt/boot-sav/sda2
/dev/sda4      vfat     1020M  490M  531M  49% /mnt/boot-sav/sda4
/dev/sda5      fuseblk   117G   46G   72G  39% /mnt/boot-sav/sda5
/dev/sda6      fuseblk    60G   20G   41G  33% /mnt/boot-sav/sda6
/dev/sda7      ext4      279G  6.0G  258G   3% /mnt/boot-sav/sda7

=================== fdisk -l:
Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 97DBBAD4-1341-11E4-827E-D43D7E6C632F

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1023999   1021952   499M Windows recovery environment
/dev/sda2    1024000   1228799    204800   100M EFI System
/dev/sda3    1228800   1490943    262144   128M Microsoft reserved
/dev/sda4    1490944   3588095   2097152     1G unknown
/dev/sda5    3588096 247946217 244358122 116.5G Microsoft basic data
/dev/sda6  850946048 976762879 125816832    60G Microsoft basic data
/dev/sda7  247947264 842723327 594776064 283.6G Linux filesystem
/dev/sda8  842723328 850946047   8222720   3.9G Linux swap

Partition table entries are not in disk order.




Disk /dev/sdb: 14.5 GiB, 15513354240 bytes, 30299520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9e04baec

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     8064 30299519 30291456 14.5G  c W95 FAT32 (LBA)


cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory
cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory
cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory
cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory
cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory
cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory
cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory
cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory
cat: /mnt/boot-sav/sda7/etc/apt/sources.list: No such file or directory


=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub-efi-amd64-signed of sda7, using the following options:     kernel-purge   sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda2/efi/.../grub*.efi file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2018-10-20
Please do not add long text.
Use the link Boot-Repairs gives or at least use Code Tags which you can add with the # icon in the Forum's advanced editor.

You show two Ubuntu UEFI boot entries, ubuntu HD and ubuntu. Do either of these boot.
What brand/model system. If those entries do not boot, then you may have one of the systems that needs a work around.
Have you updated UEFI as that often solves some issues, but you may have to redo UEFI settings as new UEFI often goes to defaults.

---

### Post by willem-v on 2018-10-22
[SOLVED] I think that is was a WUB because Oldfred says there were **two Ubuntu's** with EFI. Above that, there were more files there from my last installer of 14.04. So, formatted the USB, put only 18.04 and installer on it... and wallah. 

Thank you, Oldfred. 8-)

---

### Post by oldos2er on 2018-10-22
Would you please mark the thread Solved under Thread Tools at the top of the page? Thanks.

---

