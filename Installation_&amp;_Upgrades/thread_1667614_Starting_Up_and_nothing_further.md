---
title: "Starting Up and nothing further"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by 99digit on 2011-01-15
Somehow I managed to get rid of the errors after selecting Win XP at boot menu.

But now the problem is when i select Win XP, it goes to

Starting Up (with the cursor blinking below it)

and that's where is stops nothing further. What can be done?

you can find the boot info in my previous thread. if u need i can post it again here. please help.

---

### Post by Rubi1200 on 2011-01-15
Hi, 
please post the boot script here again and I will try and help.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Hi, 
please post the boot script here again and I will try and help.

okay here is the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /grub.cfg /boot/grub/grub.cfg 
                       /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 43006068.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    39,099,672    39,099,610  83 Linux
/dev/sda2          39,100,414   312,576,704   273,476,291   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5          39,100,416    43,005,951     3,905,536  82 Linux swap / Solaris
/dev/sda6         177,405,858   312,576,704   135,170,847   7 HPFS/NTFS
/dev/sda3    *     43,006,068   177,405,794   134,399,727   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f8748588-d670-46bb-a7bd-a9fb5c6ec61f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        8C3055F43055E5AC                       ntfs       New Volume                    
/dev/sda5        a3fb1c6d-cadd-4e47-bfc0-35287e462ad5   swap                                     
/dev/sda6        FA8861158860D225                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/New_Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /media/New_Volume_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout		30

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
# kopt=root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f8748588-d670-46bb-a7bd-a9fb5c6ec61f

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic (recovery mode)
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro  single
initrd		/boot/initrd.img-2.6.32-27-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader  +1

================================ sda1/grub.cfg: ================================

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
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
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
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
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
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda1	/	ext4	errors=remount-ro	0	1
/dev/sda3	/media/New_Volume	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda6	/media/New_Volume_	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda5	none	swap	sw	0	0
#/dev/sdb1      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdc1      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto

=================== sda1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
   4.7GB: boot/grub/grub.cfg
  10.4GB: boot/grub/menu.lst
  17.4GB: boot/grub/stage2
  18.3GB: boot/initrd.img-2.6.32-21-generic
  18.5GB: boot/initrd.img-2.6.32-27-generic
  18.1GB: boot/vmlinuz-2.6.32-21-generic
  18.3GB: boot/vmlinuz-2.6.32-27-generic
    .1GB: grub.cfg
  18.5GB: initrd.img
  18.3GB: initrd.img.old
  18.3GB: vmlinuz
  18.1GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by Rubi1200 on 2011-01-15
The problem I see is that you have a mix of GRUB-legacy (Ubuntu versions prior to 9.10) and GRUB2 (any version after 9.10).

Unless there is a particular reason for using the older version I recommend you purge and reinstall GRUB.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You must use the chroot method and mount sda1 as the Ubuntu install and install GRUB to the MBR of sda.

The reason, from what I can see in the results, that you are unable to boot Windows is that it is not being picked up by GRUB.

But, it may also have to do with the fact that XP is on an extended partition. Did you move it?

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> The problem I see is that you have a mix of GRUB-legacy (Ubuntu versions prior to 9.10) and GRUB2 (any version after 9.10).

Unless there is a particular reason for using the older version I recommend you purge and reinstall GRUB.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You must use the chroot method and mount sda1 as the Ubuntu install and install GRUB to the MBR of sda.

The reason, from what I can see in the results, that you are unable to boot Windows is that it is not being picked up by GRUB.

But, it may also have to do with the fact that XP is on an extended partition. Did you move it?

no i did not move anything, simply installed Win XP on another drive.

im following the thread you recommended, right now.

---

### Post by 99digit on 2011-01-15
ok i followed the procedure on the specified thread. now the boot menu where i used to select which OS to boot with is gone. ubuntu though is as b4.

and here is the updated boot info if u need it again:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /grub.cfg /boot/grub/grub.cfg 
                       /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 43006068.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    39,099,672    39,099,610  83 Linux
/dev/sda2          39,100,414   312,576,704   273,476,291   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5          39,100,416    43,005,951     3,905,536  82 Linux swap / Solaris
/dev/sda6         177,405,858   312,576,704   135,170,847   7 HPFS/NTFS
/dev/sda3    *     43,006,068   177,405,794   134,399,727   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f8748588-d670-46bb-a7bd-a9fb5c6ec61f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        8C3055F43055E5AC                       ntfs       New Volume                    
/dev/sda5        a3fb1c6d-cadd-4e47-bfc0-35287e462ad5   swap                                     
/dev/sda6        FA8861158860D225                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/New_Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /media/New_Volume_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout		30

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
# kopt=root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f8748588-d670-46bb-a7bd-a9fb5c6ec61f

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic (recovery mode)
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro  single
initrd		/boot/initrd.img-2.6.32-27-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader  +1

================================ sda1/grub.cfg: ================================

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
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
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
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
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
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda1	/	ext4	errors=remount-ro	0	1
/dev/sda3	/media/New_Volume	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda6	/media/New_Volume_	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda5	none	swap	sw	0	0
#/dev/sdb1      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdc1      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto

=================== sda1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  10.4GB: boot/grub/grub.cfg
   3.3GB: boot/grub/menu.lst
  17.4GB: boot/grub/stage2
  18.3GB: boot/initrd.img-2.6.32-21-generic
  18.5GB: boot/initrd.img-2.6.32-27-generic
  18.1GB: boot/vmlinuz-2.6.32-21-generic
  18.3GB: boot/vmlinuz-2.6.32-27-generic
    .1GB: grub.cfg
  18.5GB: initrd.img
  18.3GB: initrd.img.old
  18.3GB: vmlinuz
  18.1GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by Rubi1200 on 2011-01-15
Okay, there is something odd going on here.

You purged and reinstalled GRUB according to the instructions?

Yet, GRUB-legacy is still there!

Hang in there please.

I am going to ask some other members for their opinions about this.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, there is something odd going on here.

You purged and reinstalled GRUB according to the instructions?

Yet, GRUB-legacy is still there!

Hang in there please.

I am going to ask some other members for their opinions about this.

okay im hanging in here, all opinions suggestions and advice are welcome.

---

### Post by dino99 on 2011-01-15
/boot/grub/menu.lst  ***** its part of the old grub, remove it then

sudo grub-mkconfig
sudo update-grub

sudo shutdown now -R

---

### Post by 99digit on 2011-01-15
> **dino99 said:**
> /boot/grub/menu.lst  ***** its part of the old grub, remove it then

sudo grub-mkconfig
sudo update-grub

sudo shutdown now -R

you mean jus shift+del, menu.lst?
EDIT: tried to delete it, it won't let me delete the file.

and continue with the commands given?
ok will do that now.

---

### Post by dino99 on 2011-01-15
> **99digit said:**
> you mean jus shift+del, menu.lst?
EDIT: tried to delete it, it won't let me delete the file.

and continue with the commands given?
ok will do that now.

into a terminal, run:

sudo rm /boot/grub/menu.lst

then the other commands

---

### Post by 99digit on 2011-01-15
i get the boot menu now, when i select Windows, still get a blank black screen with a cursor blinking on top but nothing else is written.

---

### Post by Rubi1200 on 2011-01-15
What is the boot priority set to in BIOS?

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> What is the boot priority set to in BIOS?

boot from CD since i could boot from ubuntu live cd. otherwise ubuntu wrks smooth without the live cd also, except for windows.

---

### Post by Rubi1200 on 2011-01-15
Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

You need to repair the boot.ini file:
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by Rubi1200 on 2011-01-15
Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

I am sure there must be a way to fix this from within Ubuntu and will try and find out for you.

I assume you can boot into Ubuntu?

---

### Post by Rubi1200 on 2011-01-15
Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

I am sure there must be a way to fix this from within Ubuntu and will try and find out for you.

I assume you can boot into Ubuntu?

---

### Post by Rubi1200 on 2011-01-15
Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

See here for how to repair the boot.ini file:
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

I am sure there must be a way to fix this from within Ubuntu and will try and find out for you.

I assume you can boot into Ubuntu?

Ubuntu boots smoothly(im using it now), abt the script of watever i could understand yes 3 and 4 has XP as it says so. i dnt hav an idea how to fix boot.ini thing, hope you come with a solution for it through ubuntu.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

I am sure there must be a way to fix this from within Ubuntu and will try and find out for you.

I assume you can boot into Ubuntu?

yes i can boot into Ubuntu smoothly, hope there is a solution for editing the boot.ini through Ubuntu itself, or somehow edit it n get windows to wrk as well. thanks.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

I am sure there must be a way to fix this from within Ubuntu and will try and find out for you.

I assume you can boot into Ubuntu?

yes i can boot into Ubuntu smoothly, hope there is a solution for editing the boot.ini through Ubuntu itself, or somehow edit it n get windows to wrk as well. thanks.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

I am sure there must be a way to fix this from within Ubuntu and will try and find out for you.

I assume you can boot into Ubuntu?

yes i can boot into Ubuntu smoothly, hope there is a solution for editing the boot.ini through Ubuntu itself, or somehow edit it n get windows to wrk as well. thanks.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

I am sure there must be a way to fix this from within Ubuntu and will try and find out for you.

I assume you can boot into Ubuntu?

yes i can boot into Ubuntu smoothly, hope there is a solution for editing the boot.ini through Ubuntu itself, or somehow edit it n get windows to wrk as well. thanks.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

See here for how to repair the boot.ini file:
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

yes i can boot into Ubuntu smoothly, hope there is a solution for editing the boot.ini through Ubuntu itself, or somehow edit it n get windows to wrk as well. thanks.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

See here for how to repair the boot.ini file:
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

thanks i will follow it asap and reply.

---

### Post by 99digit on 2011-01-15
> **Rubi1200 said:**
> Okay, so here is an idea. I think the problem is with the boot.ini file and that is why you are unable to boot Windows.

If you look at the very end of the boot script results you will see what I mean.

It says XP is on partition 3 and 4, while the rest of the script says 3 and 6 (plus you have 2 entries for 4).

See here for how to repair the boot.ini file:
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

thanks i will follow it asap and reply.

sorry for the repeated replies i really don't know how this hppnd.

---

### Post by 99digit on 2011-01-16
when i insert the win setup cd there is no option to repair in it,it directly goes to the partition screen without the R=Repair option. what can i do now?

---

### Post by Rubi1200 on 2011-01-16
Well, that is odd about the Windows CD.

Anyway, if you can boot into Ubuntu or use a LiveCD, it is possible (from what I have read) to edit the boot.ini file.

Just navigate to it and open it with any text editor (you probably need root privileges to do this), change the lines to reflect the current situation and then save.

I hope that will fix things.

Ah, except that you may have to also run ```
sudo update-grub
``` in Ubuntu to make sure the changes are recognized.

---

### Post by amsterdamharu on 2011-01-16
The strange thing is that your grub.cfg seems to be missing any Windows entries but you say that it's in the menu.
I'm sure it uses old grub with menu.lst but since you've purged it and updated grub but the second boot info script output still is missing any Windows entries.
[COLOR=Red]Don't worry if you don't understand it it's for other people who might have some insight.[/COLOR]
Could you please run and post boot info script again?

Windows is on sda3, I think this would reflect to:
```
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
This because partition is suddenly not zero based anymore (I have mine on  the first partition and it says partition(1) in my boot.ini instead of  partition(0))
Not sure what set root will do to windows and if Windows would think it's on partition one when you set root to (hd0,2).

If it's wrong Windows normally comes with ....dll not found instead of a blank screen.

To edit the boot.ini you first have to start the file browser and click on computer then ???GB harddisk until you see the boot.ini.
Now start gedit by pressing alt + F2 type "sudo gedit" (no quotes) and click run. Click open and open the file. Now put the following in there:
```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2\3)\WINDOWS="Microsoft Windows XP Professional on 3" 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional on 2" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional on 1" 

```
[COLOR=Red]Now choose save as and next to the name of the file choose Windows for Line Endings[/COLOR] click save and overwrite the old boot.ini.

After grub (let's you choose Windows and Ubuntu) you get the menu in boot.ini (let's you choose Windows, Windows, Windows and Windows).

Keep pressing the down arrow button to get into this menu before it times out. You can choose "Microsoft Windows XP Professional on 3" and see if it works. If it doesn't then next time choose "Microsoft Windows XP Professional on 2" and then on 1.

If you know what works (I think 3 works) then post it here please.

---

### Post by 99digit on 2011-01-16
i edited the boot.ini 

```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2\3)\WINDOWS="Microsoft Windows XP Professional on 3" 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional on 2" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional on 1"
```

still the same problem persists, also i updated the grub with

```
sudo update-grub
```

and still the same, no errors nothing, just a cursor blinking with a blank screen.

sudo update-grub
[sudo] password for aceron: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda3
done

---

### Post by amsterdamharu on 2011-01-16
Do you get the Windows boot menu at all?
Did you try out the windows 1,2 and 3 in the Windows boot menu (it comes after grub)?

If you change timeout=1 to timeout=100 in the boot.ini you'd have more time to see it but pushing arrow up/down should cancel the timeout.

---

### Post by Rubi1200 on 2011-01-16
I definitely agree that the timeout should be set to at least the Windows default, which is 30.

@amsterdamharu: your opinion please; I was looking at the boot script again and I wonder whether this might not also be part of the problem?
```
Extended  partition  linking to another extended partition
```

---

### Post by drs305 on 2011-01-16
99digit, 

Have you addressed the partitioning issue in post #3? There is a message that partition 2 (the extended partition) overlaps partition 3 (a primary partition despite it coming last in the list).

That could very well be why you can't get Windows to work and also why the Windows repair CD goes immediately to the partitioning section rather than the boot repair one.

---

### Post by Rubi1200 on 2011-01-16
I think drs305 is right.

I did ask you previously why/how XP came to be where it is.

> /dev/sda2 overlaps with /dev/sda3
I think you need to address this issue first before tackling anything else.

I also think that before you move ahead backup all important data now just in case something goes wrong.

---

### Post by 99digit on 2011-01-16
what should i do abt the overlapping issue?

I installed XP into another drive after ubuntu 10.04.

i tried timeout with 30 and still get the same thing.

---

### Post by amsterdamharu on 2011-01-16
There is something out of the ordinary with the partition table but don't know what it is.

sda3 should have a boot sector that will display the boot.ini but I think it's gone somehow:
```
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 43006068.
```
Extended partition linking to another extended partition can't be too good either.

> Somehow I managed to get rid of the errors after selecting Win XP at boot menu.
Get rid of what errors, I am now reading from the start of the post and I wonder what started this all.
Could you start from a live CD and run gparted, I don't think it could fix it but it might give some insight of what's going on here.
Please do not resize anything just let it have a look at the disk.
To start gparted from the live cd just press alt + F2, type gparted and click run.

---

### Post by 99digit on 2011-01-16
> **amsterdamharu said:**
> There is something out of the ordinary with the partition table but don't know what it is.

sda3 should have a boot sector that will display the boot.ini but I think it's gone somehow:
```
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 43006068.
```
Extended partition linking to another extended partition can't be too good either.


Get rid of what errors, I am now reading from the start of the post and I wonder what started this all.
Could you start from a live CD and run gparted, I don't think it could fix it but it might give some insight of what's going on here.
Please do not resize anything just let it have a look at the disk.
To start gparted from the live cd just press alt + F2, type gparted and click run.

Previously whenever i selected Win XP as the OS from boot menu, i got errors like Error 12, 13 or 21. Then somehow I managed, by editing the menu.lst, and Starting Up came up but nothing further.

gparted shows me a disk of 140Gb, where as there is a 20Gb file system (has linux on it) and the other 2 partitions are ntfs.

160 GB hdd with 20GB partition of linux, rest 70Gb + 70Gb of ntfs file system.

but gparted shows 140Gb disk without any other partition or drives.

---

### Post by Rubi1200 on 2011-01-16
Please do the following:

1. post a screenshot from the LiveCD of how GParted sees the drive

2. run these commands in the terminal and post the output

```
sudo fdisk -lu

sudo sfdisk -V
```

---

### Post by 99digit on 2011-01-17
> **Rubi1200 said:**
> Please do the following:

1. post a screenshot from the LiveCD of how GParted sees the drive

2. run these commands in the terminal and post the output

```
sudo fdisk -lu

sudo sfdisk -V
```

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3fca3fc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    39099672    19549805   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2        39100414   312576704   136738145+   f  W95 Ext'd (LBA)
/dev/sda3   *    43006068   177405794    67199863+   7  HPFS/NTFS
/dev/sda5        39100416    43005951     1952768   82  Linux swap / Solaris
/dev/sda6       177405858   312576704    67585423+   7  HPFS/NTFS


```


```
sudo sfdisk -v
sfdisk (util-linux-ng 2.17.2)

```

will post the screenshot in a while.

---

### Post by 99digit on 2011-01-17
[IMG]http://i.imgur.com/Hzua5.png[/IMG]







here is the screen shot of how gparted sees the drive.

---

### Post by Rubi1200 on 2011-01-17
This thread had become quite long, so I apologize if this has been asked and answered before:
Is sda the only drive or are you also using an external one?

There is definitely a discrepancy between what GParted sees and the commands you ran.

We also still need to find a way to resolve the issue with overlapping partitions.

For the GParted issue, start by looking here:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

I have asked someone with more experience in these matters to take a look, so please wait.

Thanks for sticking with it :-)

---

### Post by 99digit on 2011-01-17
> **Rubi1200 said:**
> This thread had become quite long, so I apologize if this has been asked and answered before:
Is sda the only drive or are you also using an external one?

There is definitely a discrepancy between what GParted sees and the commands you ran.

We also still need to find a way to resolve the issue with overlapping partitions.

For the GParted issue, start by looking here:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

I have asked someone with more experience in these matters to take a look, so please wait.

Thanks for sticking with it :-)

there is no other external drive at this moment. i will always be sticking to it till i get the dual boot working. thanks for all the help till now.

and waiting for the more experienced to reply.

---

### Post by drs305 on 2011-01-17
To straighten out your partitions you may need to resort to software designed for that purpose. Of course you need to back up any important data - on a device that isn't going to affected by this.

If Windows is most important, you should consider going back to the Windows partitioning applet you've already stumbled across. I'm not a Windows expert so you should find out what it will do and what you may lose before running it.

On the Linux side, there is Test Disk. It's not the most intuitive app (I spent about 5 hours with it this weekend) but it gets the job done. Here are a couple of links explaining how to use it to restore partitions. Your situation is not exactly the same as you want to fix the sizes, not necessary find lost partitions. 

[Test Disk Step by Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")
[Herman's Test Disk HowTo]("http://members.iinet.net.au/~herman546/p21.html")

"Sticking to it" can be a great learning experience. If you are pressed for time or the need to restore your system, backing up your data and reformatting would undoubtedly be faster although you would lose your customizations.

---

### Post by srs5694 on 2011-01-17
I'm one of those Rubi1200 has asked to comment on this thread. I have some expertise in partitioning (I wrote [this page on missing partitions in GParted,](http://www.rodsbooks.com/missing-parts/index.html) which Rubi1200 referenced earlier), so that's the topic I'll tackle:

You can safely ignore the GParted output; GParted, like most or all libparted-based tools, flakes out and is useless when it encounters partitioning irregularities. Once you fix the problem, it'll work fine.

I'm starting to sour on TestDisk; it sometimes produces improperly sized extended partitions, which can produce the blank GParted results. There's another current thread in which a person used TestDisk and it created more problems than it solved. IMHO, it's a solution of last resort, and this disk isn't at that point yet.

The real problem is the overlap of /dev/sda3 (a primary partition) and /dev/sda2 (an extended partition), which is illegal. This is most easily fixed using sfdisk, in a procedure similar to that described on my Web page, by changing /dev/sda3 to /dev/sda7. This way, it will be a logical partition and it will be fine within the extended partition. The problem is that this will render Windows unbootable. Thus, a more complex fix is necessary. You can do this with sfdisk, as described on my Web page, but you'll need to make extra changes:


[list]
[*]Change /dev/sda5 to /dev/sda4 (just rename it; a cursor position, backspace over "5", and type "4").
[*]Change /dev/sda6 to /dev/sda5 (again, just rename it)
[*]Change the start point of /dev/sda2 (the extended partition) to 177405857 (one sector before the start of the new /dev/sda5)
[*]Change the size of /dev/sda2 to 135170848. That should make it big enough to cover the new /dev/sda5 (its size should be one sector greater than the size of /dev/sda5, as reported by sfdisk)
[/list]


I recommend you do a "sudo sfdisk -d /dev/sda" and make those changes. Double-check that the partitions make sense -- that they don't overlap (except for /dev/sda5, which must be contained entirely within /dev/sda2) and that your Windows boot partition is a primary partition. If you have any questions, post back, including both the original and your modified sfdisk output. If everything looks fine, write the changes back to disk.

I don't know if this will help Windows boot (that's voodoo hacking), but it should at least fix your partition table.

FWIW, my suspicion is that some Windows partitioning tool has some bugs in dealing with certain types of logical partitions and is creating such problems. I recommend extreme caution when using Windows partitioning tools!

---

### Post by drs305 on 2011-01-17
Nice *srs5694*. 

In fact, I pulled up the forum as I was backing up some partitions and working with sfdisk as I read your post.  :-)

---

### Post by 99digit on 2011-01-17
> **srs5694 said:**
> I'm one of those Rubi1200 has asked to comment on this thread. I have some expertise in partitioning (I wrote [this page on missing partitions in GParted,](http://www.rodsbooks.com/missing-parts/index.html) which Rubi1200 referenced earlier), so that's the topic I'll tackle:

You can safely ignore the GParted output; GParted, like most or all libparted-based tools, flakes out and is useless when it encounters partitioning irregularities. Once you fix the problem, it'll work fine.

I'm starting to sour on TestDisk; it sometimes produces improperly sized extended partitions, which can produce the blank GParted results. There's another current thread in which a person used TestDisk and it created more problems than it solved. IMHO, it's a solution of last resort, and this disk isn't at that point yet.

The real problem is the overlap of /dev/sda3 (a primary partition) and /dev/sda2 (an extended partition), which is illegal. This is most easily fixed using sfdisk, in a procedure similar to that described on my Web page, by changing /dev/sda3 to /dev/sda7. This way, it will be a logical partition and it will be fine within the extended partition. The problem is that this will render Windows unbootable. Thus, a more complex fix is necessary. You can do this with sfdisk, as described on my Web page, but you'll need to make extra changes:


[list]
[*]Change /dev/sda5 to /dev/sda4 (just rename it; a cursor position, backspace over "5", and type "4").
[*]Change /dev/sda6 to /dev/sda5 (again, just rename it)
[*]Change the start point of /dev/sda2 (the extended partition) to 177405857 (one sector before the start of the new /dev/sda5)
[*]Change the size of /dev/sda2 to 135170848. That should make it big enough to cover the new /dev/sda5 (its size should be one sector greater than the size of /dev/sda5, as reported by sfdisk)
[/list]


I recommend you do a "sudo sfdisk -d /dev/sda" and make those changes. Double-check that the partitions make sense -- that they don't overlap (except for /dev/sda5, which must be contained entirely within /dev/sda2) and that your Windows boot partition is a primary partition. If you have any questions, post back, including both the original and your modified sfdisk output. If everything looks fine, write the changes back to disk.

I don't know if this will help Windows boot (that's voodoo hacking), but it should at least fix your partition table.

FWIW, my suspicion is that some Windows partitioning tool has some bugs in dealing with certain types of logical partitions and is creating such problems. I recommend extreme caution when using Windows partitioning tools!

i will try to do as suggested, will report back here.

if everything goes wrong (hope not) i would install win n then try to install ubuntu.

with extreme caution i have taken a back up all the important data onto an external drive.

---

### Post by Rubi1200 on 2011-01-17
Hi 99digit,
take a deep breath before you start :)

You have made a backup; excellent!

Since you have the Windows and Ubuntu installation disks, in the worst-case scenario, you may have to start again and reinstall everything.

I hope that the instructions posted by srs5694 will see you through this though.

We will be keeping an eye on the thread and if you get stuck, please ask.

Good luck!

---

### Post by 99digit on 2011-01-19
had to format nothing went too much of a messy though. i now installed windows and will install Ubuntu using Wubi, that would be easier isn't it? and then try dual boot both. thank you all for all the help and replies.

---

### Post by 99digit on 2011-01-19
hi everybody,

 thank you for all the replies and the help you have provided me with.

installed windows, and will now install ubuntu with Wubi. I guess that is a easier way to have dual boot.

---

### Post by Rubi1200 on 2011-01-19
Just out of curiosity, did you try the method srs5694 suggested?

If you get things working and are happy with it, I wish you the best of luck.

One final point, there are problems with Wubi installs at the moment.

I have written a guide [here]("http://ubuntuforums.org/showthread.php?t=1639198").

On a fresh install of Wubi apply the method to lock the grub-pc and grub-common packages (near the end of the first post after the Permanent Fix section).

If you need any help, please ask.

---

