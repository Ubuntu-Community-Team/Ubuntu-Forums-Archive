---
title: "pls help  in solving : grub-setup: error: Cannot read `/grub/core.img' correctly"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by Khan_77 on 2010-09-02
i had installed ubuntu 9.10 on a dual boot ubuntu linux system having windows and ubuntu 9.04 then i tried to remove the swap partition of the previous ubuntu 9.04  and resize the ubuntu 9.10 partition using ubuntu livecd now i am getting grub rescue prompt showing unknown file system
 this is the output of fdisk -l 

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13003   104446566    7  HPFS/NTFS
/dev/sda2           13004       38913   208122075    f  W95 Ext'd (LBA)
/dev/sda5           13004       26006   104446566    7  HPFS/NTFS
/dev/sda6           26007       33203    57809871   83  Linux
/dev/sda7           33204       38695    44114458+  83  Linux
/dev/sda8           38696       38913     1751053+  82  Linux swap / Solaris

now when i try to  sudo grub-install --root-directory=/mnt /dev/sda7
i get this error 

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

i also tried running bootinfoscript and following is its output

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

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

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89338933

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   208,893,194   208,893,132   7 HPFS/NTFS
/dev/sda2         208,893,195   625,137,344   416,244,150   f W95 Ext d (LBA)
/dev/sda5         208,893,258   417,786,389   208,893,132   7 HPFS/NTFS
/dev/sda6         417,786,453   533,406,194   115,619,742  83 Linux
/dev/sda7         533,406,258   621,635,174    88,228,917  83 Linux
/dev/sda8         621,635,238   625,137,344     3,502,107  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AED829FFD829C705                       ntfs                                     
/dev/sda5        10C86248C8622C62                       ntfs       New Volume                    
/dev/sda6        0c33c34c-25ac-444b-8356-69d85a3f6ba5   ext3                                     
/dev/sda7        671dbc45-b13d-4b09-bd09-a29bf532785d   ext4                                     
/dev/sda8        7a28033c-3755-4077-8aaa-24e8b33abf1a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7        /mnt                     ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
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
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aed829ffd829c705
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 0c33c34c-25ac-444b-8356-69d85a3f6ba5
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=671dbc45-b13d-4b09-bd09-a29bf532785d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=7a28033c-3755-4077-8aaa-24e8b33abf1a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .8GB: boot/grub/core.img
   7.5GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
    .3GB: boot/initrd.img-2.6.31-17-generic
  34.5GB: boot/initrd.img-2.6.31-19-generic
  27.9GB: boot/initrd.img-2.6.31-20-generic
   1.3GB: boot/initrd.img-2.6.31-21-generic
  38.9GB: boot/initrd.img-2.6.31-22-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .9GB: boot/vmlinuz-2.6.31-17-generic
  37.8GB: boot/vmlinuz-2.6.31-19-generic
  23.7GB: boot/vmlinuz-2.6.31-20-generic
   7.4GB: boot/vmlinuz-2.6.31-21-generic
   1.5GB: boot/vmlinuz-2.6.31-22-generic
  38.9GB: initrd.img
   1.3GB: initrd.img.old
   1.5GB: vmlinuz
   7.4GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
#timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color yellow/light-gray white/light-gray

#A splash image for the menu
splashimage=/boot/grub/splashimages/106843-lambo-murcielago-00.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=0c33c34c-25ac-444b-8356-69d85a3f6ba5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0c33c34c-25ac-444b-8356-69d85a3f6ba5

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
# defoptions=quiet vga=769

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
# howmany=1

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

title		Ubuntu 9.04, memtest86+
uuid		0c33c34c-25ac-444b-8356-69d85a3f6ba5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=0c33c34c-25ac-444b-8356-69d85a3f6ba5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=23cec361-1f84-41a2-b3e8-4c5870367e06 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 238.5GB: boot/grub/menu.lst
 238.4GB: boot/grub/stage2

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
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
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aed829ffd829c705
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 0c33c34c-25ac-444b-8356-69d85a3f6ba5
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=671dbc45-b13d-4b09-bd09-a29bf532785d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=7a28033c-3755-4077-8aaa-24e8b33abf1a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 273.9GB: boot/grub/core.img
 280.6GB: boot/grub/grub.cfg
 273.7GB: boot/initrd.img-2.6.31-14-generic
 273.4GB: boot/initrd.img-2.6.31-17-generic
 307.6GB: boot/initrd.img-2.6.31-19-generic
 301.0GB: boot/initrd.img-2.6.31-20-generic
 274.4GB: boot/initrd.img-2.6.31-21-generic
 312.0GB: boot/initrd.img-2.6.31-22-generic
 273.7GB: boot/vmlinuz-2.6.31-14-generic
 274.0GB: boot/vmlinuz-2.6.31-17-generic
 310.9GB: boot/vmlinuz-2.6.31-19-generic
 296.8GB: boot/vmlinuz-2.6.31-20-generic
 280.5GB: boot/vmlinuz-2.6.31-21-generic
 274.6GB: boot/vmlinuz-2.6.31-22-generic
 312.0GB: initrd.img
 274.4GB: initrd.img.old
 274.6GB: vmlinuz
 280.5GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2010-09-02
The bootscript shows that GRUB is looking at sda8 which is the swap partition; that is why you are getting errors.

To reinstall GRUB2, boot the Karmic (9.10) CD and reinstall following this guide:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

The first method is the easiest. in my opinion.

You want to mount sda7 and install GRUB to sda.

Don't forget to run ```
sudo update-grub
``` after rebooting

If you have any questions, feel free to ask.

---

### Post by Khan_77 on 2010-09-02
Thanks Rubi that really worked wonders 

wonder why i had to use sda only and not sda7

thanks a lot anyways

---

### Post by Rubi1200 on 2010-09-02
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

