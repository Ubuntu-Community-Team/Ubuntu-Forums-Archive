---
title: "ubuntu boot + boot repair fail"
date: 2016-04-05
forum: Installation &amp; Upgrades
---

### Post by kalaius on 2016-04-05
Hi, 

new here and with Linux in general, seeking help with booting. Suddenly I was dropped into a grub rescue prompt when turning the computer on. After googleing, I made a live USB with boot repair. Booting took about an hour, and repair got stuck at a part where it said remove kernels and reupload last kernel. 

I don't know if I have SW or HW RAID or not. 

I have the boot info pasted in. Any advice is appreciated. 

```
f Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 1288852 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

ubuntu-vg-root: ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

ubuntu-vg-swap_1: ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   488,396,799   487,895,042   5 Extended
/dev/sda5             501,760   488,396,799   487,895,040  8e Linux LVM


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.7 GB, 15733161984 bytes
80 heads, 16 sectors/track, 24006 cylinders, total 30728832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    30,728,831    30,720,768   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       5ab1ff9e-aed2-4a9c-9c18-2b870776ed68   ext3       
/dev/mapper/ubuntu--vg-root 0e5f6af2-29bb-4bde-9c48-8b82e715f22e   ext4       
/dev/mapper/ubuntu--vg-swap_1 0cd6aa7d-842c-46de-8de9-69046248757b   swap       
/dev/sda5        UKWBPA-qZw6-9XL5-Q01O-AxZZ-nOgv-GeDCzY LVM2_member 
/dev/sdb1        A76A-0DAF                              vfat       
/dev/zram0       03066303-d05c-4299-a20c-75882aaf8fc1   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr  4 21:46 ata-WDC_WD2500AAKS-00F0A0_WD-WCAT1A007408 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr  4 21:46 ata-WDC_WD2500AAKS-00F0A0_WD-WCAT1A007408-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr  4 21:46 ata-WDC_WD2500AAKS-00F0A0_WD-WCAT1A007408-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Apr  4 21:49 dm-name-ubuntu--vg-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Apr  4 21:49 dm-name-ubuntu--vg-swap_1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr  4 21:49 dm-uuid-LVM-fo00au2MzymYysysi7gqycW9NAPzscxQXu2jj6sAR43wbEcGRt7NkiRoR6a2QiPe -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr  4 21:49 dm-uuid-LVM-fo00au2MzymYysysi7gqycW9NAPzscxQd0YsfFxSYAEZ00F6kw377NwEv2tShlkt -> ../../dm-0
lrwxrwxrwx 1 root root  9 Apr  5 17:03 usb-Kingston_DataTraveler_3.0_60A44C426697BF80E9810039-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr  4 21:46 usb-Kingston_DataTraveler_3.0_60A44C426697BF80E9810039-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Apr  4 21:46 wwn-0x50014ee1ac54b891 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr  4 21:46 wwn-0x50014ee1ac54b891-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr  4 21:46 wwn-0x50014ee1ac54b891-part5 -> ../../sda5

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
ubuntu--vg-root
ubuntu--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev             /mnt/boot-sav/mapper/ubuntu--vg-root/dev none       (rw,bind)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/ubuntu--vg-root /mnt/boot-sav/mapper/ubuntu--vg-root ext4       (rw)
/dev/pts         /mnt/boot-sav/mapper/ubuntu--vg-root/dev/pts none       (rw,bind)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2

00000000  8c 54 48 f2 b6 8a 85 15  2d 9c 8c 2e 45 6c d6 3c  |.TH.....-...El.<|
00000010  b4 5b 8b 66 cc 63 c8 ea  86 ee c7 bf 4a 94 31 f8  |.[.f.c......J.1.|
00000020  f3 b9 9d 45 3c 88 b5 fb  d4 33 fc 5a 50 66 ee cd  |...E<....3.ZPf..|
00000030  1f 5c 3a 9e a1 a4 6b 50  01 e1 13 06 d2 44 17 af  |.\:...kP.....D..|
00000040  91 d0 e3 93 b7 bb 60 e9  83 86 c8 60 b2 7b 45 c1  |......`....`.{E.|
00000050  11 c7 e4 9c 29 03 3f a4  77 0c 04 38 a5 72 5f 99  |....).?.w..8.r_.|
00000060  01 8c 97 48 16 98 42 14  fe d3 8b 39 25 72 49 3d  |...H..B....9%rI=|
00000070  a8 27 e8 a5 b8 bd 8d c2  2b 3b 05 d9 60 ff 38 5c  |.'......+;..`.8\|
00000080  df 83 a7 67 4e 41 4e ae  0f c9 6d ee 7c 96 7b a1  |...gNAN...m.|.{.|
00000090  9b 0b cd 62 61 27 fc d7  61 51 ea 01 7d 43 c7 4e  |...ba'..aQ..}C.N|
000000a0  6c 97 dd e5 d4 3d 64 68  07 4b df 07 3d bb 55 4d  |l....=dh.K..=.UM|
000000b0  8f 94 72 e0 4e ed 26 24  d5 89 3f 46 ed f2 01 6f  |..r.N.&$..?F...o|
000000c0  41 74 08 0f 5b 9d 16 3e  7b 76 19 f9 7c 6d a3 a1  |At..[..>{v..|m..|
000000d0  6c 6f ea fa 8c 40 0b d3  2e 10 ab ff 43 ef 21 6d  |lo...@......C.!m|
000000e0  95 38 68 cc 71 87 e3 a2  41 6f 81 68 b8 96 16 95  |.8h.q...Ao.h....|
000000f0  51 5e a4 62 b0 01 97 37  ae f3 1f b4 0a 16 b7 ae  |Q^.b...7........|
00000100  51 af 96 62 b5 9e 50 6a  a0 ac 3a 89 bf ef 14 77  |Q..b..Pj..:....w|
00000110  ac 12 8b 64 32 5f b5 76  8d 1a 35 9a 98 51 4c 91  |...d2_.v..5..QL.|
00000120  f7 81 52 ab a3 71 0a b1  3f 94 9f 4a cd f4 c1 83  |..R..q..?..J....|
00000130  e4 96 b8 40 ef c0 3d e8  ac c2 68 2d 3d 39 02 6e  |...@..=...h-=9.n|
00000140  bd 8f a2 02 de 27 70 87  52 0a 9a 88 04 50 ff ed  |.....'p.R....P..|
00000150  64 ca e4 39 f1 f7 3d 7f  d4 31 85 ac 5d 4c 07 2f  |d..9..=..1..]L./|
00000160  9e 54 cf 3f 38 d5 3b af  08 3d 4e af 12 d8 c1 3b  |.T.?8.;..=N....;|
00000170  cc f7 f1 60 7a 35 06 c7  f2 a4 bb 55 e5 59 75 3d  |...`z5.....U.Yu=|
00000180  a4 f0 e5 48 7c 68 82 8b  7e e5 d3 6b 2b de a8 61  |...H|h..~..k+..a|
00000190  60 a1 d1 77 37 8b 80 5b  8c 78 2c 2d 6a 34 0f b1  |`..w7..[.x,-j4..|
000001a0  53 41 c3 f0 7b cb 4a 4e  85 9e d5 65 4f 9c 49 2c  |SA..{.JN...eO.I,|
000001b0  e3 8a 53 0c 8d 31 57 96  61 c8 40 dd fe aa 00 3b  |..S..1W.a.@....;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 b0 14 1d 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on ubuntu-vg-root


Unknown BootLoader on ubuntu-vg-swap_1



=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
hexdump: /dev/sda1: Input/output error
hexdump: /dev/sda1: Input/output error
File descriptor 9 (/proc/26157/mounts) leaked on lvs invocation. Parent PID 10050: bash
File descriptor 63 (pipe:[80858]) leaked on lvs invocation. Parent PID 10050: bash
  /dev/sda1: read failed after 0 of 4096 at 0: Input/output error
File descriptor 9 (/proc/26157/mounts) leaked on lvchange invocation. Parent PID 15746: bash
File descriptor 63 (pipe:[80858]) leaked on lvchange invocation. Parent PID 15746: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root
  /dev/sda1: read failed after 0 of 4096 at 0: Input/output error
  Volume group "ubuntu-vg-root" not found
  Skipping volume group ubuntu-vg-root
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
File descriptor 9 (/proc/26157/mounts) leaked on lvchange invocation. Parent PID 15746: bash
File descriptor 63 (pipe:[80858]) leaked on lvchange invocation. Parent PID 15746: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1
  /dev/sda1: read failed after 0 of 4096 at 0: Input/output error
  Volume group "ubuntu-vg-swap_1" not found
  Skipping volume group ubuntu-vg-swap_1
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-info 2016-04-05__16h46 ===================
boot-info version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
BLKID BEFORE LVM ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="5ab1ff9e-aed2-4a9c-9c18-2b870776ed68" TYPE="ext3"
/dev/sda5: UUID="UKWBPA-qZw6-9XL5-Q01O-AxZZ-nOgv-GeDCzY" TYPE="LVM2_member"
/dev/sdb1: UUID="A76A-0DAF" TYPE="vfat"
/dev/zram0: UUID="03066303-d05c-4299-a20c-75882aaf8fc1" TYPE="swap"
/dev/mapper/ubuntu--vg-root: UUID="0e5f6af2-29bb-4bde-9c48-8b82e715f22e" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="0cd6aa7d-842c-46de-8de9-69046248757b" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/26157/mounts) leaked on vgscan invocation. Parent PID 26168: /bin/bash
Reading all physical volumes.  This may take a while...
/dev/sda1: read failed after 0 of 4096 at 0: Input/output error
Found volume group "ubuntu-vg" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/26157/mounts) leaked on vgchange invocation. Parent PID 26168: /bin/bash
/dev/sda1: read failed after 0 of 4096 at 0: Input/output error
2 logical volume(s) in volume group "ubuntu-vg" now active
File descriptor 9 (/proc/26157/mounts) leaked on lvscan invocation. Parent PID 26168: /bin/bash
/dev/sda1: read failed after 0 of 4096 at 0: Input/output error
LVSCAN:
ACTIVE            '/dev/ubuntu-vg/root' [224.64 GiB] inherit
ACTIVE            '/dev/ubuntu-vg/swap_1' [8.00 GiB] inherit
Is there RAID on this computer? yes

BLKID BEFORE RAID ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="5ab1ff9e-aed2-4a9c-9c18-2b870776ed68" TYPE="ext3"
/dev/sda5: UUID="UKWBPA-qZw6-9XL5-Q01O-AxZZ-nOgv-GeDCzY" TYPE="LVM2_member"
/dev/sdb1: UUID="A76A-0DAF" TYPE="vfat"
/dev/zram0: UUID="03066303-d05c-4299-a20c-75882aaf8fc1" TYPE="swap"
/dev/mapper/ubuntu--vg-root: UUID="0e5f6af2-29bb-4bde-9c48-8b82e715f22e" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="0cd6aa7d-842c-46de-8de9-69046248757b" TYPE="swap"
dmraid -si -c: no raid disks
No DMRAID disk.
RAID került detektálásra A [mdadm] csomagok telepítése után érdemes újra próbálnia. (sudo apt-get install -y --force-yes mdadm --no-install-recommends)
Warning: no DMRAID nor MD_ARRAY.
File descriptor 9 (/proc/26157/mounts) leaked on lvs invocation. Parent PID 427: /bin/sh
/dev/sda1: read failed after 0 of 4096 at 0: Input/output error
boot-info is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --  debian-installer/language=hu keyboard-configuration/layoutcode?=hu
[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
Set sda as corresponding disk of mapper/ubuntu--vg-root
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

=================== os-prober:
/dev/mapper/ubuntu--vg-root:Ubuntu 14.04.4 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="5ab1ff9e-aed2-4a9c-9c18-2b870776ed68" TYPE="ext3"
/dev/sda5: UUID="UKWBPA-qZw6-9XL5-Q01O-AxZZ-nOgv-GeDCzY" TYPE="LVM2_member"
/dev/sdb1: UUID="A76A-0DAF" TYPE="vfat"
/dev/zram0: UUID="03066303-d05c-4299-a20c-75882aaf8fc1" TYPE="swap"
/dev/mapper/ubuntu--vg-root: UUID="0e5f6af2-29bb-4bde-9c48-8b82e715f22e" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="0cd6aa7d-842c-46de-8de9-69046248757b" TYPE="swap"

[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
Set sda as corresponding disk of mapper/ubuntu--vg-root

1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== mapper/ubuntu--vg-root/etc/grub.d/ :
drwxr-xr-x  2 root root         4096 febr   3 19:03 grub.d
total 76
-rwxr-xr-x 1 root root  9791 dec   17 15:00 00_header
-rwxr-xr-x 1 root root  6058 máj   13  2015 05_debian_theme
-rwxr-xr-x 1 root root 11608 jún   26  2015 10_linux
-rwxr-xr-x 1 root root 10412 jún   26  2015 20_linux_xen
-rwxr-xr-x 1 root root  1992 márc  12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 jún   26  2015 30_os-prober
-rwxr-xr-x 1 root root  1416 jún   26  2015 30_uefi-firmware
-rwxr-xr-x 1 root root   214 jún   26  2015 40_custom
-rwxr-xr-x 1 root root   216 jún   26  2015 41_custom
-rw-r--r-- 1 root root   483 jún   26  2015 README




=================== mapper/ubuntu--vg-root/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
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



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
mapper/ubuntu--vg-root    : sda,    not-sepboot,    no-grubenv    grub2,    grub-pc ,    update-grub,    64,    no-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/ubuntu--vg-root.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD2500AAKS-0 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
1      1049kB  256MB  255MB  primary                boot
2      257MB   250GB  250GB  extended
5      257MB   250GB  250GB  logical                lvm


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4129kB  15.7GB  15.7GB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 241GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
1      0.00B  241GB  241GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8586MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
1      0.00B  8586MB  8586MB  linux-swap(v1)


                                                                            Error: /dev/zram0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA WDC WD2500AAKS-0;
1:1049kB:256MB:255MB:::boot;
2:257MB:250GB:250GB:::;
5:257MB:250GB:250GB:::lvm;

BYT;
/dev/sdb:15.7GB:scsi:512:512:msdos:Kingston DataTraveler 3.0;
1:4129kB:15.7GB:15.7GB:fat32::boot, lba;

BYT;
/dev/mapper/ubuntu--vg-root:241GB:dm:512:512:loop:Linux device-mapper (linear);
1:0.00B:241GB:241GB:ext4::;

BYT;
/dev/mapper/ubuntu--vg-swap_1:8586MB:dm:512:512:loop:Linux device-mapper (linear);
1:0.00B:8586MB:8586MB:linux-swap(v1)::;

                                                                            Error: /dev/zram0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/mapper/ubuntu--vg-root on /mnt/boot-sav/mapper/ubuntu--vg-root type ext4 (rw)
/dev on /mnt/boot-sav/mapper/ubuntu--vg-root/dev type none (rw,bind)
/dev/pts on /mnt/boot-sav/mapper/ubuntu--vg-root/dev/pts type none (rw,bind)
/proc on /mnt/boot-sav/mapper/ubuntu--vg-root/proc type none (rw,bind)
/run on /mnt/boot-sav/mapper/ubuntu--vg-root/run type none (rw,bind)
/sys on /mnt/boot-sav/mapper/ubuntu--vg-root/sys type none (rw,bind)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 ecryptfs fd full fuse fw0 hidraw0 hidraw1 hpet input kmsg kvm log mapper mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout ubuntu-vg uhid uinput urandom vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control ubuntu--vg-root ubuntu--vg-swap_1
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

=================== df -Th:

Filesystem                  Type       Size  Used Avail Use% Mounted on
/cow                        overlayfs  976M  307M  618M  34% /
/dev                        none       3.9G   12K  3.9G   1% /mnt/boot-sav/mapper/ubuntu--vg-root/dev
/run                        none       799M  1.1M  798M   1% /mnt/boot-sav/mapper/ubuntu--vg-root/run
/dev/sdb1                   vfat        15G  1.7G   14G  11% /cdrom
/dev/loop0                  squashfs   549M  549M     0 100% /rofs
none                        tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs                       tmpfs      3.9G   16K  3.9G   1% /tmp
none                        tmpfs      5.0M     0  5.0M   0% /run/lock
none                        tmpfs      3.9G     0  3.9G   0% /run/shm
none                        tmpfs      100M   16K  100M   1% /run/user
/dev/mapper/ubuntu--vg-root ext4       221G  200G  9.8G  96% /mnt/boot-sav/mapper/ubuntu--vg-root

=================== fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c92b6

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sdb: 15.7 GB, 15733161984 bytes
80 heads, 16 sectors/track, 24006 cylinders, total 30728832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00049c34

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    30728831    15360384    c  W95 FAT32 (LBA)

Disk /dev/mapper/ubuntu--vg-root: 241.2 GB, 241210228736 bytes
255 heads, 63 sectors/track, 29325 cylinders, total 471113728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-swap_1: 8585 MB, 8585740288 bytes
255 heads, 63 sectors/track, 1043 cylinders, total 16769024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to enable-raid enable-lvm) and reinstall the grub2 of mapper/ubuntu--vg-root into the MBR of sda, using the following options:     kernel-purge
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2016-04-05
It looks like you have LVM which is an advanced logical partition scheme that is inside the normal physical partitions.
It is required if you chose the full drive encryption.

Do not know LVM nor encryption.
But if encrypted, you need to mount the LVM & encrypted logical partitions using your passphase for Boot-Repair to work.
And if encrypted you need to develop a very good backup plan as recovery of encrypted partitions is difficult or impossible. And you must know passphrase for anything to work.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

