---
title: "Grub2 recovery after windows7"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by tpsa on 2011-03-27
After windows 7 installtion (I have forgotten to backup mbr), I tried to recover grub (from [http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala) tutorial) but every time I try, after rebooting (grub had installed itself properly) during booting grub drops to the grub shell (I have correctly generated grub.cfg file by grub-mkconfig).

What I am doing wrongly?

---

### Post by Quackers on 2011-03-27
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tpsa on 2011-03-29
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD 
                       /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,579,449    24,579,387  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     24,579,450   105,643,439    81,063,990   7 HPFS/NTFS
/dev/sda3         182,112,901   976,768,064   794,655,164   f W95 Ext d (LBA)
/dev/sda5    *    182,112,903   264,140,729    82,027,827  83 Linux
/dev/sda6         264,140,793   288,495,269    24,354,477  82 Linux swap / Solaris
/dev/sda7         288,495,333   965,763,539   677,268,207  83 Linux
/dev/sda8         965,763,603   976,768,064    11,004,462  83 Linux
/dev/sda4         105,643,440   182,096,774    76,453,335  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        2EA08398A0836565                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1   ext3                                     
/dev/sda5        cdc70c74-1daa-44fc-a7ce-7a9aefd077c3   ext4                                     
/dev/sda6        c0b16065-036d-46da-9dec-117a1031f80e   swap                                     
/dev/sda7        2871bb3c-6907-438f-ac5e-40bf08916a60   ext4       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /live/image              iso9660    (ro,noatime)
/dev/sda2        /mnt                     ntfs       (rw)


=========================== sda5/boot/grub/menu.lst: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
set locale_dir=($root)/boot/grub/locale
set lang=pl
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=cdc70c74-1daa-44fc-a7ce-7a9aefd077c3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=cdc70c74-1daa-44fc-a7ce-7a9aefd077c3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3c98-ac5d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2ea08398a0836565
	chainloader +1
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (on /dev/sda4)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
	linux /boot/vmlinuz-2.6.35.8 root=UUID=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1 ro quiet splash
	initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (recovery mode) (on /dev/sda4)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
	linux /boot/vmlinuz-2.6.35.8 root=UUID=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1 ro single
	initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, memtest86+ (on /dev/sda4)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
set locale_dir=($root)/boot/grub/locale
set lang=pl
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=cdc70c74-1daa-44fc-a7ce-7a9aefd077c3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=cdc70c74-1daa-44fc-a7ce-7a9aefd077c3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set cdc70c74-1daa-44fc-a7ce-7a9aefd077c3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3c98-ac5d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2ea08398a0836565
	chainloader +1
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (on /dev/sda4)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
	linux /boot/vmlinuz-2.6.35.8 root=UUID=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1 ro quiet splash
	initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (recovery mode) (on /dev/sda4)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
	linux /boot/vmlinuz-2.6.35.8 root=UUID=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1 ro single
	initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, memtest86+ (on /dev/sda4)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda7       /home           ext4    errors=remount-ro  0      1
# swap was on /dev/sda6 during installation
UUID=c0b16065-036d-46da-9dec-117a1031f80e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 129.8GB: boot/grub/grub.cfg
 106.6GB: boot/grub/menu.lst
 129.8GB: boot/grub/stage2
  94.8GB: boot/initrd.img-2.6.35-28-generic
 130.0GB: boot/vmlinuz-2.6.35-28-generic
  94.8GB: initrd.img
 130.0GB: vmlinuz

=========================== sda4/boot/grub/menu.lst: ===========================

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
timeout		10

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
# kopt=root=UUID=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1/boot/grub/splash.xpm.gz

title		BackTrack 4 R2, kernel 2.6.35.8
uuid		8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
kernel		/boot/vmlinuz-2.6.35.8 root=UUID=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.35.8
quiet

title		BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid		8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
kernel		/boot/vmlinuz-2.6.35.8 root=UUID=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1 ro  single
initrd		/boot/initrd.img-2.6.35.8

title		BackTrack 4 R2, memtest86+
uuid		8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8df4e7e4-d5a2-4dfd-a8b5-05ed8d6727d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c0b16065-036d-46da-9dec-117a1031f80e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda7       /home           ext4        user,exec

=================== sda4: Location of files loaded by Grub: ===================


  86.5GB: boot/grub/menu.lst
  86.6GB: boot/grub/stage2
  86.6GB: boot/initrd.img-2.6.35.8
  86.7GB: boot/vmlinuz-2.6.35.8
  86.6GB: initrd.img
  86.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 7e 3c  |<.~<.~<.~<.~<.~<|
00000010  00 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
00000020  7e 3c 00 7e 3c 00 7e 3c  00 7e 3c 00 7e 3c 00 7e  |~<.~<.~<.~<.~<.~|
00000030  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 7e 3c  |<.~<.~<.~<.~<.~<|
00000040  00 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
00000050  7e 3c 00 7e 3c 00 7e 3c  00 7e 3c 00 7e 3c 00 7e  |~<.~<.~<.~<.~<.~|
00000060  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 7e 3c  |<.~<.~<.~<.~<.~<|
00000070  00 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
00000080  7e 3c 00 7e 3c 00 7e 3c  00 7e 3c 00 7e 3c 00 7e  |~<.~<.~<.~<.~<.~|
00000090  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 7e 3c  |<.~<.~<.~<.~<.~<|
000000a0  00 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
000000b0  7e 3c 00 7e 3c 00 7e 3c  01 7f 3d 02 81 3f 04 84  |~<.~<.~<..=..?..|
000000c0  41 06 83 40 07 83 40 06  81 3f 04 80 3d 02 7e 3c  |A..@..@..?..=.~<|
000000d0  01 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
000000e0  7e 3c 00 7e 3c 00 7e 3c  00 7e 3c 00 7e 3c 00 7e  |~<.~<.~<.~<.~<.~|
000000f0  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 7e 3c  |<.~<.~<.~<.~<.~<|
00000100  00 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
00000110  7e 3c 00 7e 3c 00 7e 3c  00 7e 3c 00 7e 3c 00 7e  |~<.~<.~<.~<.~<.~|
00000120  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 7e 3c  |<.~<.~<.~<.~<.~<|
00000130  00 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
00000140  7e 3c 00 7e 3c 00 7e 3c  00 7e 3c 00 7e 3c 00 7e  |~<.~<.~<.~<.~<.~|
00000150  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 7e 3c  |<.~<.~<.~<.~<.~<|
00000160  00 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
00000170  7e 3c 00 7e 3c 00 7e 3c  00 7e 3c 00 7e 3c 00 7e  |~<.~<.~<.~<.~<.~|
00000180  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 7e 3c  |<.~<.~<.~<.~<.~<|
00000190  00 7e 3c 00 7e 3c 00 7e  3c 00 7e 3c 00 7e 3c 00  |.~<.~<.~<.~<.~<.|
000001a0  7e 3c 00 7e 3c 00 7e 3c  00 7e 3c 00 7e 3c 00 7e  |~<.~<.~<.~<.~<.~|
000001b0  3c 00 7e 3c 00 7e 3c 00  7e 3c 00 7e 3c 00 80 fe  |<.~<.~<.~<.~<...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 33 a5 e3 04 00 fe  |..........3.....|
000001d0  ff ff 05 fe ff ff 35 a5  e3 04 ec 9e 73 01 00 00  |......5.....s...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda8

00000000  31 60 36 bd a8 41 f0 46  f5 6c eb d0 8b 34 8e 10  |1`6..A.F.l...4..|
00000010  ba 21 dc 24 9b 25 0c 24  65 00 16 c0 01 a0 44 57  |.!.$.%.$e.....DW|
00000020  10 68 b7 5d fa 8a d5 f9  ef 3c fe 47 c5 17 07 e7  |.h.].....<.G....|
00000030  69 d1 96 5f 0d 60 67 73  3a 1d d1 6c bd 73 3b 97  |i.._.`gs:..l.s;.|
00000040  0b a6 51 37 18 13 6f 7f  29 fd b1 06 6a 2e 3a 86  |..Q7..o.)...j.:.|
00000050  60 6a 29 54 ae 40 6a fd  1d 49 2f 73 69 1f 10 2a  |`j)T.@j..I/si..*|
00000060  a3 c0 d9 2c 70 a6 1b 08  e9 c5 30 2a 97 ed 2a 19  |...,p.....0*..*.|
00000070  6e 1d c2 dc 66 27 51 fb  12 f4 27 60 41 1d b1 7f  |n...f'Q...'`A...|
00000080  c6 ec d7 fb 4c 9b 80 56  6f b2 e3 d2 04 82 7a d0  |....L..Vo.....z.|
00000090  1f 80 4b df ed 43 06 6d  9b aa cb 1b af 76 c8 55  |..K..C.m.....v.U|
000000a0  2a 92 ff 8f 9e 66 b1 41  3a 7c f7 19 54 28 d8 7a  |*....f.A:|..T(.z|
000000b0  83 70 88 91 e5 de f2 39  60 49 38 25 0e c7 56 ed  |.p.....9`I8%..V.|
000000c0  f9 26 7f b6 a6 40 e2 ce  0c 49 65 4c a6 32 94 7f  |.&...@...IeL.2..|
000000d0  ea 10 b2 52 b7 a5 eb 3e  f3 12 92 7e 14 c7 5d 0b  |...R...>...~..].|
000000e0  bc c4 94 e5 71 80 3f ad  3f f8 1e dc 06 53 d5 4a  |....q.?.?....S.J|
000000f0  0a 5f 25 44 03 e4 3d 79  18 62 51 5c 21 15 56 29  |._%D..=y.bQ\!.V)|
00000100  02 5f 94 90 2e 65 58 5b  7a 2d e7 e8 ed b2 c0 78  |._...eX[z-.....x|
00000110  d6 7a a1 65 f0 54 17 2d  0a 90 af 3a 4a af 26 1f  |.z.e.T.-...:J.&.|
00000120  c9 2c 07 a1 dc c7 d3 05  16 e9 50 1b 6f 35 ed 67  |.,........P.o5.g|
00000130  ed 13 8f cb 91 bb 5c 20  b2 34 5e fe 7f 2b d5 95  |......\ .4^..+..|
00000140  4f f3 74 9d c8 4b 5e 7c  88 48 54 2e ed a1 54 e3  |O.t..K^|.HT...T.|
00000150  59 c0 ac 0f d3 ec bf 2b  87 f0 21 18 00 bc 96 7d  |Y......+..!....}|
00000160  7d ed 76 6e 23 ad e1 29  07 d4 18 25 de 6c 90 ac  |}.vn#..)...%.l..|
00000170  96 17 58 a4 d2 75 27 90  60 90 97 05 72 bb e1 08  |..X..u'.`...r...|
00000180  05 10 d7 94 3e 7d ab 90  93 c0 dd f7 51 b3 df 41  |....>}......Q..A|
00000190  fa 8d b9 e4 23 c4 ee 50  54 e3 b7 d4 b2 f2 df db  |....#..PT.......|
000001a0  24 ad 8f 31 e1 86 db 3d  4c f8 bb a0 5a fc e0 c4  |$..1...=L...Z...|
000001b0  43 47 ad 17 f9 2b e0 a0  57 62 52 02 1e fd d7 14  |CG...+..WbR.....|
000001c0  22 5f 0d c7 5e 59 7d 1f  1f 09 41 63 24 7c b2 ed  |"_..^Y}...Ac$|..|
000001d0  ef f4 07 e0 97 31 e3 e0  65 8c b8 34 24 20 d9 08  |.....1..e..4$ ..|
000001e0  40 46 aa 5e e5 01 ba 97  72 36 39 48 77 f8 17 93  |@F.^....r69Hw...|
000001f0  dc 56 bc 7c 4f 9f 05 c6  de 3d 61 5c 99 57 22 89  |.V.|O....=a\.W".|
00000200




```

The last partition is crypted

---

