---
title: "here it is again GRUB error 17"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by cocokiwi on 2008-11-15
OLD hat! same problem!

ASUS M2N32-SLI  4 gig..GTX 280

2 x 1 tb in RAID strip config!
1 x 300 gig/1 80 gig, and a 1 TB external

I managed to get Vista 64bit back again!
and I have WinXP 32 bit on a partition in the 300 gig! I would have liked to put UB on the raid?
I think GRUB is trying to put it in the Raid first Drive instead of the Second D drive..win 32 partition,and cannot be accessed because of the RAID config! It's not space thats the problem(ducking)

Here is the way I had it with Docs(grin):lolflag:


Darn It! 8.10 Is a real pain! with "GRUB" will someone FIX it! Please!! 

1 > fix it so GRUB goes directly to Edit mode when detecting an error or a means 
to do so!
2 > PUT! access to GRUB in the MENU on the CD so one can access it without having 
to load Ubuntu...

The problems with GRUB transend 8.10 and long ago..THERE are MANY complaints about this PROBLEM and MANY posts on this subject!

My biggest is compatiblity with RAID, WHY is RAID not supported DIRECTLY..:confused:
1 > recognize the RAID setup:)

2 > Ask if you wish to install on a unused 
    partition,just as it do now!:)

3 > Is it too hard or what! right now one has to 
     be a NASA geek to figure it out.
    and I,m not the only one compaining(whining)  
    or is it (wimpering) ](*,)

So WHEN! is someone going to get off his butt and fix it so we do not have these problems. I thought windows was bad (Ducking)

Dennis McMillan

I have TWO 1 TB Seagate Drives set as RAID stripe, Main C drive WinVista64bit.

WHY! is there NO way directly from the CDs INSTALL to go into a RAID setup and put "ubuntu" in a RAID partition??? Then I might get it to work,Maybe!

I have another drive 300 gig that is NOT raid with another copy of WinXP 32 ...this will be the Secondry copy! once I shoehorn a copy of XP 64bit and then overlay VISTA 64bit..(DONE)
NOW! another drive 80 gig with Linux on it! got a drive all by itself! right now reduntant(removed!

EVERY time I install LINUX..I get a GRUB 17 error when I start!

Here is the DOC stuff: figure it out,I,m still a begineer at this!

*-disk:0 
description: ATA Disk
product: ST31000340AS
vendor: Seagate
physical id: 0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: SD15
serial: 9QJ10AKQ
size: 931GiB (1TB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=00fa00fa
*-disk:1
description: ATA Disk
product: ST31000340AS
vendor: Seagate
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/sdb
version: SD15
serial: 9QJ1V8N7
size: 931GiB (1TB)
configuration: ansiversion=5
*-disk
description: ATA Disk
product: Maxtor 6V300F0
vendor: Maxtor
physical id: 0
bus info: scsi@2:0.0.0
logical name: /dev/sdc
version: VA11
serial: V603BQ9G
size: 279GiB (300GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=4225f361
*-cdrom
description: DVD writer
product: DVDR PX-755A
vendor: PLEXTOR
physical id: 1
bus info: scsi@3:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/scd0
logical name: /dev/sr0
logical name: /cdrom
version: 1.08
capabilities: removable audio cd-r cd-rw dvd dvd-r
configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
*-medium
physical id: 0
logical name: /dev/cdrom
logical name: /cdrom
configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
*-disk
description: ATA Disk
product: WDC WD800JD-60LU
vendor: Western Digital
physical id: 0.0.0
bus info: scsi@5:0.0.0
logical name: /dev/sdd
version: 07.0
serial: WD-WMAMD3125801
size: 74GiB (80GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=00033baa
*-disk
description: SCSI Disk
product: Stylus Storage
vendor: EPSON
physical id: 0.0.0
bus info: scsi@12:0.0.0
logical name: /dev/sde
version: 1.00
capabilities: removable
configuration: ansiversion=2
*-medium
physical id: 0
logical name: /dev/sde
*-disk
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@11:0.0.0
logical name: /dev/sdf
size: 3831MiB (4017MB)
capabilities: partitioned partitioned:dos
configuration: signature=c3072e18
*-disk:0
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@10:0.0.0
logical name: /dev/sdg
*-disk:1
description: SCSI Disk
physical id: 0.0.1
bus info: scsi@10:0.0.1
logical name: /dev/sdh
*-disk:2
description: SCSI Disk
physical id: 0.0.2
bus info: scsi@10:0.0.2
logical name: /dev/sdi
*-disk:3
description: SCSI Disk
physical id: 0.0.3
bus info: scsi@10:0.0.3
logical name: /dev/sdj
*-disk
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@13:0.0.0
logical name: /dev/sdk
size: 931GiB (1TB)
capabilities: partitioned partitioned:dos
configuration: signature=a4b57300
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK Change partition table
fdisk -l [-b SSZ] [-u] DISK List partition table(s)
fdisk -s PARTITION Give partition size(s) in blocks
fdisk -v Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00fa00fa

Device Boot Start End Blocks Id System
/dev/sda1 * 1 33146 266240000 7 HPFS/NTFS
/dev/sda2 33146 130032 778240000 7 HPFS/NTFS
/dev/sda3 130032 243203 909042688 7 HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
omitting empty partition (5)

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4225f361

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 17722 142350941 7 HPFS/NTFS
/dev/sdc2 17723 35441 142321059 f W95 Ext'd (LBA)
/dev/sdc5 17723 35441 142321027+ 7 HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033baa

Device Boot Start End Blocks Id System
/dev/sdd1 1 9327 74919096 83 Linux
/dev/sdd2 9328 9729 3229065 5 Extended
/dev/sdd5 9328 9729 3229033+ 82 Linux swap / Solaris

Disk /dev/sdf: 4017 MB, 4017618944 bytes
218 heads, 32 sectors/track, 1124 cylinders
Units = cylinders of 6976 * 512 = 3571712 bytes
Disk identifier: 0xc3072e18

Device Boot Start End Blocks Id System
/dev/sdf1 * 1 1125 3923440 c W95 FAT32 (LBA)

Disk /dev/sdk: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xa4b57300

Device Boot Start End Blocks Id System
/dev/sdk1 1278906 1938021 332194464 7 HPFS/NTFS
/dev/sdk2 1 620065 312512413+ 7 HPFS/NTFS
/dev/sdk3 620065 1278905 332055517+ 7 HPFS/NTFS

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 


# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cfebba9d-ffe7-404e-b629-c9354c91ca6f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cfebba9d-ffe7-404e-b629-c9354c91ca6f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid cfebba9d-ffe7-404e-b629-c9354c91ca6f
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cfebba9d-ffe7-404e-b629-c9354c91ca6f ro quiet splash 
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid cfebba9d-ffe7-404e-b629-c9354c91ca6f
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cfebba9d-ffe7-404e-b629-c9354c91ca6f ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid cfebba9d-ffe7-404e-b629-c9354c91ca6f
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Windows NT/2000/XP (loader)
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1  


Thanks :popcorn:

---

