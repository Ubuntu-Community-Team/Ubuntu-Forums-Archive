---
title: "Reverting to 8.04"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by alanwalterthomas on 2012-09-19
I have 12.04, but just installed 8.04 on an disused old IDE disk to run some commercial programs that don't work in 12.04. After a problem free install of 8.04 to the old IDE disk, I updated grub2 from 12.04, and (5) 8.04 entries appear in grub's boot selection list during boot, but selecting them leads to: 

error: no such device
error: no such partition
error: you need to load the kernel first.

I can still boot to 12.04 & Win7 without any trouble. Any idea what's going on & how to get my install to work?

---

### Post by coffeecat on 2012-09-19
We need certain information about your system which the boot info script can provide. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script in your Ubuntu 12.04 - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

It's interesting that you have five entries for 8.04 after a fresh install. I would expect only 2, but hopefully the boot script will tell us why.

Also - one thing to check. Make sure the old ide drive is still being seen in the BIOS.

---

### Post by alanwalterthomas on 2012-09-20
My disk setup
2 identical 640 GB primary disks.
Linux uses one RAID1 partition, a RAID0 partition & swap. I have Win7 on one disk, and a backup of its partition on the other.
Besides this, I have the 40 GB Maxtor IDE drive, where I installed 8.04 on a small 6.xy GB partition, and the rest is just extra storage for 12.04.

Thank you very much for any help!

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/6653d57681626d940fc3b4d0e21d2f5b)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/6653d57681626d940fc3b4d0e21d2f5b)/boot/grub on this drive.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdc3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

md0: ___________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md1: ___________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   108,214,271   108,007,424  fd Linux raid autodetect
/dev/sda3         108,215,856 1,250,263,727 1,142,047,872   5 Extended
/dev/sda5         108,216,320 1,065,244,671   957,028,352  fd Linux raid autodetect
/dev/sda6       1,235,224,576 1,250,263,039    15,038,464  82 Linux swap / Solaris
/dev/sda7       1,065,254,148 1,235,221,784   169,967,637   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
16 heads, 63 sectors/track, 1240341 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   185,303,039   185,300,992   7 NTFS / exFAT / HPFS
/dev/sdb2         185,303,040   293,310,463   108,007,424  fd Linux raid autodetect
/dev/sdb3         293,312,510 1,250,263,039   956,950,530   5 Extended
/dev/sdb5         293,312,512 1,250,263,039   956,950,528  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 40.0 GB, 40025947648 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78175679 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048    64,571,391    64,569,344  83 Linux
/dev/sdc2    *     64,581,300    77,593,949    13,012,650  83 Linux
/dev/sdc3          77,593,950    78,172,289       578,340  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/md0         c3187065-c59c-49cb-87ac-25b0b4e64245   ext4       System
/dev/md1         9ee89ecb-49e3-4e92-8bba-ae81e5805bd7   ext4       Data
/dev/sda1        CA2C72652C724C87                       ntfs       System Reserved
/dev/sda2        6653d576-8162-6d94-0fc3-b4d0e21d2f5b   linux_raid_member 
/dev/sda5        96516611-7645-41a0-fb99-832abdc032db   linux_raid_member 
/dev/sda6        c42f4b96-1590-4f69-a513-f5c34720d914   swap       
/dev/sda7        fd6b140e-d11c-44bc-910c-fc7e86081124   ext4       Win7Backup
/dev/sdb1        CE16645616644217                       ntfs       
/dev/sdb2        6653d576-8162-6d94-0fc3-b4d0e21d2f5b   linux_raid_member 
/dev/sdb5        96516611-7645-41a0-fb99-832abdc032db   linux_raid_member 
/dev/sdc1        1945952b-a460-42cc-b4ee-11cb6a197d88   ext4       Old40GBDrive
/dev/sdc2        ba0bfc72-3114-49ab-89b1-73f5fb7c276f   ext3       
/dev/sdc3        90a31ae3-432d-468e-b40b-a0737104ac94   swap       
/dev/sr0                                                iso9660    Ubuntu 8.04.4 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro)
/dev/md1         /home                    ext4       (rw)
/dev/sr0         /media/Ubuntu 8.04.4 amd64 iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


=========================== sdc2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# kopt=root=UUID=ba0bfc72-3114-49ab-89b1-73f5fb7c276f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=ba0bfc72-3114-49ab-89b1-73f5fb7c276f ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=ba0bfc72-3114-49ab-89b1-73f5fb7c276f ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,1)
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

--------------------------------------------------------------------------------

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=ba0bfc72-3114-49ab-89b1-73f5fb7c276f /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda3
UUID=90a31ae3-432d-468e-b40b-a0737104ac94 none            swap    sw              0       0
# /dev/sda6
UUID=c42f4b96-1590-4f69-a513-f5c34720d914 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  33.375558853 = 35.836733440   boot/grub/menu.lst                             1
  33.375528336 = 35.836700672   boot/grub/stage2                               2
  33.181142807 = 35.627980800   boot/initrd.img-2.6.24-26-generic              4
  33.188829422 = 35.636234240   boot/vmlinuz-2.6.24-26-generic                 2
  33.181142807 = 35.627980800   initrd.img                                     4
  33.188829422 = 35.636234240   vmlinuz                                        2

=========================== md0/boot/grub/grub.cfg: ============================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod raid
insmod mdraid09
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod raid
  insmod mdraid09
  insmod part_msdos
  insmod part_msdos
  insmod ext2
  set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
  search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=4
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	linux	/boot/vmlinuz-3.2.0-31-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro   quiet splash acpi_skip_timer_override hpet=force clocksource=hpet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	echo	'Loading Linux 3.2.0-31-generic ...'
	linux	/boot/vmlinuz-3.2.0-31-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-31-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro   quiet splash acpi_skip_timer_override hpet=force clocksource=hpet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro   quiet splash acpi_skip_timer_override hpet=force clocksource=hpet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	echo	'Loading Linux 3.2.0-27-generic ...'
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro   quiet splash acpi_skip_timer_override hpet=force clocksource=hpet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	echo	'Loading Linux 3.2.0-26-generic ...'
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro   quiet splash acpi_skip_timer_override hpet=force clocksource=hpet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	echo	'Loading Linux 3.2.0-25-generic ...'
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro   quiet splash acpi_skip_timer_override hpet=force clocksource=hpet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/6653d57681626d940fc3b4d0e21d2f5b)'
	search --no-floppy --fs-uuid --set=root c3187065-c59c-49cb-87ac-25b0b4e64245
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root CA2C72652C724C87
	chainloader +1
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /vmlinuz root=/dev/sdc2
	initrd /initrd.img
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /vmlinuz root=/dev/sdc2
	initrd /initrd.img
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /boot/vmlinuz-2.6.24-26-generic root=/dev/sdc2
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /vmlinuz root=/dev/sdc2
	initrd /initrd.img
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /vmlinuz root=/dev/sdc2
	initrd /initrd.img
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
--------------------------------------------------------------------------------

================================ md0/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=c3187065-c59c-49cb-87ac-25b0b4e64245 /               ext4    errors=remount-ro 0       1
# /home was on /dev/md1 during installation
UUID=9ee89ecb-49e3-4e92-8bba-ae81e5805bd7 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c42f4b96-1590-4f69-a513-f5c34720d914 none            swap    sw              0       0
# NFS from router
#192.168.1.1:/jffs/STORAGE /mnt/nfs_router nfs rw,hard,intr 0 0
--------------------------------------------------------------------------------

==================== md0: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  58.183830261 = 62.474412032   boot/grub/core.img                             1
   8.132293701 = 8.731983872    boot/grub/grub.cfg                             1
  11.022262573 = 11.835064320   boot/initrd.img-3.2.0-24-generic               2
  16.049266815 = 17.232769024   boot/initrd.img-3.2.0-25-generic               2
  18.771743774 = 20.156006400   boot/initrd.img-3.2.0-26-generic               2
  89.732654572 = 96.349704192   boot/initrd.img-3.2.0-27-generic               2
  97.256092072 = 104.427933696  boot/initrd.img-3.2.0-29-generic               2
   8.553134918 = 9.183858688    boot/initrd.img-3.2.0-31-generic               1
  12.602283478 = 13.531598848   boot/vmlinuz-3.2.0-24-generic                  2
  13.555412292 = 14.555013120   boot/vmlinuz-3.2.0-25-generic                  1
  10.160869598 = 10.910150656   boot/vmlinuz-3.2.0-26-generic                  2
  21.328842163 = 22.901669888   boot/vmlinuz-3.2.0-27-generic                  2
  80.535873413 = 86.474735616   boot/vmlinuz-3.2.0-29-generic                  1
  95.660873413 = 102.715080704  boot/vmlinuz-3.2.0-31-generic                  1
   8.553134918 = 9.183858688    initrd.img                                     1
  97.256092072 = 104.427933696  initrd.img.old                                 2
  95.660873413 = 102.715080704  vmlinuz                                        1
  80.535873413 = 86.474735616   vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

---

### Post by coffeecat on 2012-09-21
This error:

> **alanwalterthomas said:**
> 
error: no such device
error: no such partition
error: you need to load the kernel first.

Is probably explained by the following. Your boot script output shows that the Ubuntu 8.04 entries in your Ubuntu 12.04 grub.cfg file are as follows:

```
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /vmlinuz root=/dev/sdc2
	initrd /initrd.img
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /vmlinuz root=/dev/sdc2
	initrd /initrd.img
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /boot/vmlinuz-2.6.24-26-generic root=/dev/sdc2
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /vmlinuz root=/dev/sdc2
	initrd /initrd.img
}
menuentry "Ubuntu 8.04.4 LTS (8.04) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set=root f5737069-7872-45a1-9c1b-0540d4e8d3aa
	linux /vmlinuz root=/dev/sdc2
	initrd /initrd.img
}
```

The /dev/sdc2 and (hd2,msdos2) are correct, but the UUID for the 8.04 root partition - f5737069-7872-45a1-9c1b-0540d4e8d3aa - is incorrect. Compare with the blkid output:

```

Device           UUID                                   TYPE       LABEL

/dev/md0         c3187065-c59c-49cb-87ac-25b0b4e64245   ext4       System
/dev/md1         9ee89ecb-49e3-4e92-8bba-ae81e5805bd7   ext4       Data
/dev/sda1        CA2C72652C724C87                       ntfs       System Reserved
/dev/sda2        6653d576-8162-6d94-0fc3-b4d0e21d2f5b   linux_raid_member 
/dev/sda5        96516611-7645-41a0-fb99-832abdc032db   linux_raid_member 
/dev/sda6        c42f4b96-1590-4f69-a513-f5c34720d914   swap       
/dev/sda7        fd6b140e-d11c-44bc-910c-fc7e86081124   ext4       Win7Backup
/dev/sdb1        CE16645616644217                       ntfs       
/dev/sdb2        6653d576-8162-6d94-0fc3-b4d0e21d2f5b   linux_raid_member 
/dev/sdb5        96516611-7645-41a0-fb99-832abdc032db   linux_raid_member 
/dev/sdc1        1945952b-a460-42cc-b4ee-11cb6a197d88   ext4       Old40GBDrive
/dev/sdc2        ba0bfc72-3114-49ab-89b1-73f5fb7c276f   ext3       
/dev/sdc3        90a31ae3-432d-468e-b40b-a0737104ac94   swap       
/dev/sr0                                                iso9660    Ubuntu 8.04.4 amd64

```

The UUID in your grub.cfg file does not exist.

I'd suggest running "sudo update-grub" within Ubuntu 12.04 again in order to regenerate your grub.cfg file, but it sounds as though you have already done this. Try it again and see if the UUIDs in the 8.04 entries change.

A couple of things. The 8.04 entries don't look the way they usually appear when update-grub is run and I don't understand why there are 5 of them. Also - the boot script output doesn't list any kernels from your 8.04 installation. While in 12.04, mount the 8.04 sdc2 partition and have a look in the /boot folder in that partition. Are there any kernel files?

Last thing - I have no real experience of RAID so I don't know whether having 12.04 on RAID and 8.04 on a separate single drive may be a factor.

---

### Post by snowpine on 2012-09-21
Could it be as simple as the 8.04 kernel doesn't support ext4 filesystem and you need an ext3 /boot partition?

---

### Post by coffeecat on 2012-09-21
> **snowpine said:**
> Could it be as simple as the 8.04 kernel doesn't support ext4 filesystem and you need an ext3 /boot partition?

According to the boot script output, 8.04 is on sdc2 which is ext3 and has the /boot directory. However, it would be interesting to know what sdc1 was intended for, as that is formatted ext4.

---

### Post by alanwalterthomas on 2012-09-21
Got it! Writing this from 8.04. Thanks!

sdc1 is just extra space to store data for 12.04.

That actually turned out to be part of the reason I couldn't log in. I long ago disabled IDE in BIOS to speed up boot a little. By the time I put in the IDE drive, I had forgotten that, and for some reason I was able to access the drive from 12.04, and install 8.04 without any problem.

I enabled IDE again in the BIOS, and everything worked.

By the way, I also ran update-grub again, and it produced different output with just the 8.04, 8.04 recovery, and memtest options, even though I'm *certain* I had run it earlier after install 8.04.

Thanks a lot for bringing up the point about IDE in BIOS.

---

