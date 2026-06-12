---
title: "Dual Boot Problem: 9.10 boots Xp hangs."
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Paulgirardin on 2010-01-27
I have just installed Karmic on a dual boot system with XP and Ubuntu on separate drives.This set up worked ok with Jaunty.

When the boot menu comes up, selecting Linux results in a successful boot.
Selecting "Windows XP home edition (on /dev/sda1)" results in the screen changing to blank with the word "Grub" in the top left corner and no further progress.No error codes associated with this message.

I've tried suggestions I've seen in various threads but have had no success.

Below is the contents of menu.lst:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9e76c341-c736-480d-97de-42b98a899726

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Paulgirardin on 2010-01-27
9.10 is installed on sdb1
Xp is installed on sda1


Below are the results of the Boot Info Script:

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=9e76c341-c736-480d-97de-42b98a899726)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 3248391 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b159b15

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    73,400,984    73,400,922   7 HPFS/NTFS
/dev/sda2          73,400,985   115,346,699    41,945,715   7 HPFS/NTFS
/dev/sda3         115,346,700   976,768,064   861,421,365   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x988d3358

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    41,945,714    41,945,652  83 Linux
/dev/sdb2          41,945,715    83,891,429    41,945,715  83 Linux
/dev/sdb3          83,891,430    88,084,394     4,192,965  82 Linux swap / Solaris
/dev/sdb4          88,084,395   976,768,064   888,683,670  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01296a69

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   125,837,144   125,837,082   7 HPFS/NTFS
/dev/sdc2         125,837,145   488,392,064   362,554,920  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C8E4918CE4917CFE                       ntfs       sda1 System: Windows XP       
/dev/sda2        9E78DC3F78DC17BB                       ntfs       sda2 Windows XP Data 20 GiB   
/dev/sda3        763C238B3C234609                       ntfs       sda3 ext4 410 GiB             
/dev/sdb1        9e76c341-c736-480d-97de-42b98a899726   ext4                                     
/dev/sdb2        7debcd00-c230-49f4-9170-e92d6f4b5511   ext4                                     
/dev/sdb3        038f845b-864f-49de-80a6-f3f4d8ebffd1   swap                                     
/dev/sdb4        fecc606e-0d64-4e2d-a7a6-5588ad690660   ext4       sdb4 ext4 Linux               
/dev/sdc1        493F70286530D035                       ntfs       sdc1 ntfs 60 GiB              
/dev/sdc2        f3a988f0-2aec-45c7-836d-6cde235a1075   ext4       sdc2 ext4 172 Gi              

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

aufs             /                aufs       (rw)
/dev/sr0         /cdrom           iso9660    (rw)
/dev/loop0       /rofs            squashfs   (rw)
/dev/sdb1        /media/9e76c341-c736-480d-97de-42b98a899726 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb2        /media/7debcd00-c230-49f4-9170-e92d6f4b5511 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb4        /media/sdb4      Linux      type
/dev/sdc1        /media/sdc1      60         GiB
/dev/sdc2        /media/sdc2      172        Gi


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9e76c341-c736-480d-97de-42b98a899726

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 9e76c341-c736-480d-97de-42b98a899726
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9e76c341-c736-480d-97de-42b98a899726
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9e76c341-c736-480d-97de-42b98a899726
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c8e4918ce4917cfe
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=9e76c341-c736-480d-97de-42b98a899726 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=7debcd00-c230-49f4-9170-e92d6f4b5511 /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=038f845b-864f-49de-80a6-f3f4d8ebffd1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  69 6a 29 01 00 00 00 01  |........ij).....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 1a 1f 80 07 00 fe  |......?.........|
000001d0  ff ff 83 fe ff ff 59 1f  80 07 28 26 9c 15 00 00  |......Y...(&....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Paulgirardin on 2010-01-27
This is an entry in the Grub.cfg file:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c8e4918ce4917cfe
	drivemap -s (hd0) ${root}
	chainloader +1

I don't know if this is the problem.Should I change this?

---

### Post by Paulgirardin on 2010-01-27
Bump

---

### Post by Paulgirardin on 2010-01-27
Any help?

---

### Post by Leppie on 2010-01-27
was karmic a clean install or upgrade?

---

### Post by oldfred on 2010-01-27
It looks like you did have wubi installed as windows show that file. You also have grub installed to the  windows PBR partition boot record. 

Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 3248391 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.

This overwrote the standard windows boot loader that has to be in the PBR for windows to boot. You also have grub in sda and the ubuntu install in sdb. It would be better to have the grub installed to sdb and change the BIOS to boot from sdb. Then you could reinstall the windows boot loader to sda and run the repairs on the windows install to fix the windows PBR and MBR.

In your working ubuntu to install grub2 to sdb.
sudo dpkg-reconfigure grub-pc

This will give you several screens to editing changes to the grub config file which you can just accept. When it asks for drive to install to select sdb.

While sda is still the boot drive use your windows CD to run the repairs to fix windows boot. Make sure it boots ok and then switch drives in BIOS to have the grub2 in sdb boot. Run update grub to let it find the windows install.

sudo update-grub

to fix windows XP
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by Paulgirardin on 2010-01-27
> **Leppie said:**
> was karmic a clean install or upgrade?

Karmic was a clean install.

---

### Post by Paulgirardin on 2010-01-27
> **oldfred said:**
> It looks like you did have wubi installed as windows show that file. You also have grub installed to the  windows PBR partition boot record. 

Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 3248391 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.

This overwrote the standard windows boot loader that has to be in the PBR for windows to boot. You also have grub in sda and the ubuntu install in sdb. It would be better to have the grub installed to sdb and change the BIOS to boot from sdb. Then you could reinstall the windows boot loader to sda and run the repairs on the windows install to fix the windows PBR and MBR.

In your working ubuntu to install grub2 to sdb.
sudo dpkg-reconfigure grub-pc

This will give you several screens to editing changes to the grub config file which you can just accept. When it asks for drive to install to select sdb.

While sda is still the boot drive use your windows CD to run the repairs to fix windows boot. Make sure it boots ok and then switch drives in BIOS to have the grub2 in sdb boot. Run update grub to let it find the windows install.

sudo update-grub

to fix windows XP
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

Thanks for the suggestions.I will try them shortly and post the results.
:p

---

### Post by Leppie on 2010-01-27
follow oldfred's instructions to rebuild your windows boot loader.
after which you need to install grub2 to one of your mbr's. you can choose to change the boot order in your systems bios and leave the windows disk with the default mbr and install grub2 to the mbr of sdb.
to re-install grub to the mbr, boot off the livecd and issue these commands:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sdb  ##or /dev/sda if you do not want to change the boot order in the bios
```

---

### Post by Paulgirardin on 2010-01-28
> **Leppie said:**
> follow oldfred's instructions to rebuild your windows boot loader.
after which you need to install grub2 to one of your mbr's. you can choose to change the boot order in your systems bios and leave the windows disk with the default mbr and install grub2 to the mbr of sdb.
to re-install grub to the mbr, boot off the livecd and issue these commands:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck /dev/sdb  ##or /dev/sda if you do not want to change the boot order in the bios
```

Thanks Leppie,
I will do this after the usual back-ups .

---

### Post by Paulgirardin on 2010-01-29
I opened the XP Recovery Consul; performed the FIXMBR C: & FIXBOOT C: commands.
The COPY D:\I386\NTLDR\ C:\ & COPY D:\I386\NTDETECT.COM C:\ both resulted in "ACCESS DENIED" messages.
I did not perform the BOOTCFG /rebuild.
I rebooted the computer and booted into XP successfully.
I had a little sound problem,which corrected when I checked the sound driver.(I saw this when I installed 9.04 - corrected when I rebooted windows a second time.)

Rebooted into 9.10 with no problems.

Obviously,I haven't altered the location of Grub2 (sda1).

Do you still recommend that I reinstall Grub2 to sdb?

---

### Post by Leppie on 2010-01-29
> **Paulgirardin said:**
> Do you still recommend that I reinstall Grub2 to sdb?
that is completely up to you. the advantage of having grub on the linux disk is that if you remove the linux disk, windows will boot normally without any further intervention. as a positive side effect the linux drive will boot normally if you put it in another pc with the same system specs or if you remove the windows drive.
hence in the event that one of the drives should fail, at least the other system should be bootable like this.

i just noticed  an error in the install command:
```
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```

---

### Post by Paulgirardin on 2010-01-29
> **Leppie said:**
> that is completely up to you. the advantage of having grub on the linux disk is that if you remove the linux disk, windows will boot normally without any further intervention. as a positive side effect the linux drive will boot normally if you put it in another pc with the same system specs or if you remove the windows drive.
hence in the event that one of the drives should fail, at least the other system should be bootable like this.

i just noticed  an error in the install command:
```
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```

Am I correct to assume:

sudo mount /dev/sdb1 /mnt

Is still to be issued before:

sudo grub-install --recheck --root-directory=/mnt /dev/sdb


Edit:
Ok,the above is confirmed in this thread:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=install+grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=install+grub2)

I'm wondering if I should uninstall the existing Grub2 with:

sudo apt-get purge grub2 grub-pc

Before reinstalling Grub2 on sdb

---

### Post by oldfred on 2010-01-30
***No** *you do not want to uninstall the grub2 software. The install of the grub2 bootloader into the MBR is just a small part of the software that can be located on any drive's MBR. With multiple drives it is better to have the grub bootloader in the MBR of the drive with Ubuntu as leppie said above. There also has been a minor bug in grub2 where it takes an extra 10-20 seconds  to scan partitions before the menu when it is on a different drive.

---

### Post by Paulgirardin on 2010-01-30
The system will now boot either OS on either drive.(when selected in Bios)


For this problem the fix was: 

In XP Recovery Console:

FIXMBR C: 
FIXBOOT C: 

In Live CD Terminal:

sudo mount /dev/sdb1 /mnt

sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

(one small error in the last command: "/" after "mnt")


Many thanks to Oldfred and Leppie for their help

=D>=D>=D>

---

