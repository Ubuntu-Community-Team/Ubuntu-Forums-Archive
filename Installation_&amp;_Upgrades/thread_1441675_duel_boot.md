---
title: "duel boot"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by alton2536 on 2010-03-29
please help .lost my grub/ boot . 2 hard drives one with xp other with Ubuntu. tried adding window 7 to xp drive and lost every thing!! (never again) Removed 7 restored mbr via xp disc, but on startup get " MINIMAL BASH LINE EDITING IS SUPPORTED. THEN SH:GRUB. ??
[U]               Boot Info Script 0.55    dated February 15th, 2010                    

[/U]> ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=2bd8650c-e304-40e6-bf06-29571284ee3d)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1         163,959,390   306,729,044   142,769,655   f W95 Ext d (LBA)
/dev/sda5         163,959,453   306,729,044   142,769,592   7 HPFS/NTFS
/dev/sda2    *        112,455   163,959,389   163,846,935   7 HPFS/NTFS
/dev/sda3         306,729,045   312,496,379     5,767,335  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0eebd9fa

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   f W95 Ext d (LBA)
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x170a8ae2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065   625,137,344   625,121,280   f W95 Ext d (LBA)
/dev/sdc5              16,128   625,137,344   625,121,217   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        061CC9C01CC9AACF                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda5        166051663FA6C011                       ntfs                                     
/dev/sdb1        2bd8650c-e304-40e6-bf06-29571284ee3d   ext3                                     
/dev/sdb5        b54eb76a-4d2f-4d0a-8fb3-96eba6867c6a   swap                                     
/dev/sdc5        82583DB3583DA6B7                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/2bd8650c-e304-40e6-bf06-29571284ee3d ext3       (rw,nosuid,nodev,uhelper=devkit)


================================ sda2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN 

=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2bd8650c-e304-40e6-bf06-29571284ee3d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-21-generic
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-18-generic
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-18-generic (recovery mode)
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro  single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=2bd8650c-e304-40e6-bf06-29571284ee3d ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        2bd8650c-e304-40e6-bf06-29571284ee3d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=2bd8650c-e304-40e6-bf06-29571284ee3d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b54eb76a-4d2f-4d0a-8fb3-96eba6867c6a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  71.8GB: boot/grub/core.img
  71.8GB: boot/grub/menu.lst
  71.8GB: boot/grub/stage2
  71.8GB: boot/initrd.img-2.6.31-14-generic
  71.9GB: boot/initrd.img-2.6.31-15-generic
  71.8GB: boot/initrd.img-2.6.31-16-generic
  71.9GB: boot/initrd.img-2.6.31-17-generic
  71.8GB: boot/initrd.img-2.6.31-18-generic
  71.8GB: boot/initrd.img-2.6.31-19-generic
  71.9GB: boot/initrd.img-2.6.31-20-generic
  71.9GB: boot/initrd.img-2.6.31-21-generic
  71.9GB: boot/vmlinuz-2.6.31-14-generic
  71.8GB: boot/vmlinuz-2.6.31-15-generic
  71.8GB: boot/vmlinuz-2.6.31-16-generic
  71.8GB: boot/vmlinuz-2.6.31-17-generic
  71.9GB: boot/vmlinuz-2.6.31-18-generic
  71.8GB: boot/vmlinuz-2.6.31-19-generic
  71.9GB: boot/vmlinuz-2.6.31-20-generic
  71.9GB: boot/vmlinuz-2.6.31-21-generic
  71.9GB: initrd.img
  71.9GB: initrd.img.old
  71.9GB: vmlinuz
  71.9GB: vmlinuz.old

---

### Post by alton2536 on 2010-03-29
Hi all
It looks like i'am getting no where! i believe i have two grub types, is this the problem? 

[U]=>[COLOR=Red] Grub 2[/COLOR] is installed in the MBR of /dev/sda and looks for 
    (UUID=2bd8650c-e304-40e6-bf06-29571284ee3d)/boot/grub.
 =>[COLOR=Red] Grub 2[/COLOR] is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => [COLOR=Red]Grub 0.97[/COLOR] is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

[/U]Now do i need the delete oneor the other ??

i would guess that grub/boot needs to be on_[COLOR=Red]/dev/sdb1                  63   149,838,254   149,838,192  83 Linux [/COLOR] _as this would be where grub/boot should be ??

Am I correct , if so how do I do it please.

---

