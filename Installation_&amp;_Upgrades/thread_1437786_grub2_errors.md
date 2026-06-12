---
title: "grub2 errors"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by skidaddy on 2010-03-24
i am using Ubuntu 9.04 dual boot windoz xp set up a new drive with multiply partions and installed Ubuntu beta 10.04 on first one.  New drive  is on sabrent sata card. seems to work fine reads and can mount partions in 9.04 fine.  Grub 2 can not find drive. it does not show up in bios listing.  how do i find what drive to set as root  (hdo) or the like when selected gives must load kernal first error.

---

### Post by oldfred on 2010-03-24
Compters boot from the drive set as primary Master in BIOS (SATA) or jumpers on hard drive for primary master (IDE). 
If the BIOS cannot see the drive, then I do not think there is a way to boot from it.

---

### Post by skidaddy on 2010-03-24
You could be right but is there a way you can find out which disk it is the (hd0) part since grub 2.  it really seems it is confused about it once it is up and running the sata drive is listed as sda while the ide drive is moved to sdb

---

### Post by oldfred on 2010-03-24
This will show what is installed where but does not show the BIOS.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by skidaddy on 2010-03-24
here is info.  looks like i have errors on some of my disks.  although it seems to work fine.   I forgot to says thanks for your help.  I think you are right about the bios making it unbootable from the start I think maybe its time to by a new motherboard which i want to do anyway. its just when i get into something like this i spend every waking moment on it and it drives me more insane than normal.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 1.96 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 355454253.
    Operating System:  
    Boot files/dirs:   

################################
### That is the new sata drive  
### Follows is the listing for my old drive which is still the main Disk drive
###  with 9.04 on it my system boots fine on 9.04 and xp
################################

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb6 starts at sector 116439183.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   216,845,369   216,845,307  83 Linux
/dev/sda3         341,477,702   804,037,184   462,559,483   5 Extended
/dev/sda5         341,477,703   355,454,189    13,976,487  82 Linux swap / Solaris
/dev/sda6         355,454,253   804,037,184   448,582,932   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd6bad6ba

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    64,211,804    64,211,742   7 HPFS/NTFS
/dev/sdb3         112,374,737   320,159,384   207,784,648   f W95 Ext d (LBA)
/dev/sdb5         112,374,738   116,439,119     4,064,382  82 Linux swap / Solaris
/dev/sdb6         116,439,183   227,673,179   111,233,997   7 HPFS/NTFS
/dev/sdb7         227,673,243   320,159,384    92,486,142  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e18762be-4c0a-4193-aab0-163b0f7fc22b   ext3       Ubuntu10                      
/dev/sda5        c092dc3c-1d8f-48ef-98c8-90a45d273001   swap                                     
/dev/sda6        EA45-B63A                              vfat       Data                          
/dev/sdb1        1A5CC7D95CC7ADB7                       ntfs       XP_Pro                        
/dev/sdb5        a8da8a54-c25c-4dbf-9030-83c406f301b3   swap                                     
/dev/sdb6        C60E75920E757C6D                       ntfs       oldxp                         
/dev/sdb7        d2baa21f-56c9-4ce8-9079-6093617773c4   ext3       9.04                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb7        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb6        /media/oldxp             fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=512)
/dev/sda6        /media/DataX2            vfat       (rw,noexec,nosuid,nodev,uid=1000,umask=077,utf8)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e18762be-4c0a-4193-aab0-163b0f7fc22b
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e18762be-4c0a-4193-aab0-163b0f7fc22b
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e18762be-4c0a-4193-aab0-163b0f7fc22b
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=e18762be-4c0a-4193-aab0-163b0f7fc22b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e18762be-4c0a-4193-aab0-163b0f7fc22b
	echo	Loading Linux 2.6.32-16-generic ...
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=e18762be-4c0a-4193-aab0-163b0f7fc22b ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e18762be-4c0a-4193-aab0-163b0f7fc22b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e18762be-4c0a-4193-aab0-163b0f7fc22b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 1a5cc7d95cc7adb7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04 OLD DRIVE, kernel 2.6.28-18-generic (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d2baa21f-56c9-4ce8-9079-6093617773c4
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro quiet splash
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d2baa21f-56c9-4ce8-9079-6093617773c4
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro single
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d2baa21f-56c9-4ce8-9079-6093617773c4
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e18762be-4c0a-4193-aab0-163b0f7fc22b /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c092dc3c-1d8f-48ef-98c8-90a45d273001 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=a8da8a54-c25c-4dbf-9030-83c406f301b3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 107.4GB: boot/grub/core.img
 107.5GB: boot/grub/grub.cfg
 107.4GB: boot/initrd.img-2.6.32-16-generic
 107.4GB: boot/vmlinuz-2.6.32-16-generic
 107.4GB: initrd.img
 107.4GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


=========================== sdb7/boot/grub/menu.lst: ===========================

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
default         1

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
# kopt=root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d2baa21f-56c9-4ce8-9079-6093617773c4

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
##      altoptions=(single-user) single
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

title		Chainload into GRUB 2
uuid		d2baa21f-56c9-4ce8-9079-6093617773c4
kernel		/boot/grub/core.img

##title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
##root
		
##title		When you have verified GRUB 2 works, you can use this command to
##root

##title		complete the upgrade:  upgrade-from-grub-legacy
##root

##title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
##root

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		d2baa21f-56c9-4ce8-9079-6093617773c4
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro quiet splash
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		d2baa21f-56c9-4ce8-9079-6093617773c4
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro single
initrd		/boot/initrd.img-2.6.28-18-generic


title		Ubuntu 10.04, kernel 2.6.32-16-generic
uuid		e18762be-4c0a-4193-aab0-163b0f7fc22b
kernel		/boot/vmlinuz-2.6.32-16-generic
root=UUID=e18762be-4c0a-4193-aab0-163b0f7fc22b ro quiet splash
initrd		/boot/initrd.img-2.6.32-16-generic

title		Debian GNU/Linux, kernel memtest86+
root		d2baa21f-56c9-4ce8-9079-6093617773c4
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# on

title		Ubuntu 10.04, kernel 2.6.32-16 chain
uuid         e18762be-4c0a-4193-aab0-163b0f7fc22b
kernel	     /boot/grub/core.img

title		Ubuntu 10.04, kernel 2.6.32-16 chain2
root         (hd1,0)
kernel	     /boot/grub/core.img

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 10.04,/dev/sda1- kernel 2.6.32-16-generic
root           (hd0)
kernel		/boot/vmlinuz-2.6.32-16-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.32-16-generic


###################
###### made several changes trying to get to boot to jump to 10.04
###### in above and even in one below  yes i read the do not edit but you can edit it
###### using (hd1) or (hd1,x) gives -does not exist error - using the UUid does same 
####################

=========================== sdb7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,7)
search --fs-uuid --set d2baa21f-56c9-4ce8-9079-6093617773c4
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,7)
search --fs-uuid --set d2baa21f-56c9-4ce8-9079-6093617773c4
menuentry "Ubuntu, linux 2.6.28-18-generic" {
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro splash #GRUB_DISABLE_LINUX_UUID=true quiet splash
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-18-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro single splash #GRUB_DISABLE_LINUX_UUID=true
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic" {
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro splash #GRUB_DISABLE_LINUX_UUID=true quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 ro single splash #GRUB_DISABLE_LINUX_UUID=true
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-16-generic (on /dev/sda1)" {
	linux /boot/vmlinuz-2.6.32-16-generic root=/dev/sda1 ro quiet splash
	initrd /boot/initrd.img-2.6.32-16-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	set root=(hd0,1)
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (CHAIN TO /sda1)" {
	set root=/dev/sda1
	chainloader +1
}

### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=d2baa21f-56c9-4ce8-9079-6093617773c4 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a8da8a54-c25c-4dbf-9030-83c406f301b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb6 	/media/oldxp   ntfs-3g  auto,users,uid=1000,gid=100,fmask=137,utf8  0 0
/dev/sda6	/media/DataX2	vfat	auto,users,uid=1000,umask=077,utf8	0	0

=================== sdb7: Location of files loaded by Grub: ===================


 158.3GB: boot/grub/core.img
 158.4GB: boot/grub/grub.cfg
 158.3GB: boot/grub/menu.lst
 158.4GB: boot/initrd.img-2.6.28-11-generic
 158.4GB: boot/initrd.img-2.6.28-18-generic
 158.3GB: boot/vmlinuz-2.6.28-11-generic
 158.3GB: boot/vmlinuz-2.6.28-18-generic
 158.4GB: initrd.img
 158.4GB: initrd.img.old
 158.3GB: vmlinuz
 158.3GB: vmlinuz.old

---

