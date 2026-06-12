---
title: "Kernel Panic -not syncing"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by Esilvanio on 2014-09-03
Hi,

i'm here to request an help this community and forum :(:(, after normal upgrade software to my dell studio 1555 with kubuntu 12.04 i received this error:

```
Kernel panic - not syncing: VFS:Unable to mount root fs on unkbnown-block(0,0)
```

entering into grub menu i have this voices

```
(hd0,0) (hd0,msdos1) (hd0,mdos2)
```

i'm entered with live usb and i can see all from hdd i hava launch a script to have all informations about boot and i copy here to give more informations

```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 2174168 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 8.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   616,824,831   616,822,784  83 Linux
/dev/sda2         616,826,878   625,141,759     8,314,882   5 Extended
/dev/sda5         616,826,880   625,141,759     8,314,880  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              8     7,831,551     7,831,544   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        c829136a-7740-4a11-837e-aa5797607acc   ext4       
/dev/sda5        cdb2c20e-cf52-4bff-90e4-84dd09002c29   swap       
/dev/sdb1        CAEB-7260                              vfat       
/dev/sdc1        5151-764A                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/kubuntu/c829136a-7740-4a11-837e-aa5797607acc ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/kubuntu/5151-764A vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,flush,uhelper=udisks2)


=========================== sda1/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
  set locale_dir=($root)/boot/grub/locale
  set lang=
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 75,75,75; then
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
menuentry 'Ubuntu, with Linux 3.2.0-68-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-68-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-68-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-68-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-68-generic ...'
	linux	/boot/vmlinuz-3.2.0-68-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-68-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-65-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-65-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-65-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-65-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-65-generic ...'
	linux	/boot/vmlinuz-3.2.0-65-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-65-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-64-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-64-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-64-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-64-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-64-generic ...'
	linux	/boot/vmlinuz-3.2.0-64-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-64-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-61-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-61-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-61-generic ...'
	linux	/boot/vmlinuz-3.2.0-61-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-61-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-59-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-59-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-59-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-59-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-59-generic ...'
	linux	/boot/vmlinuz-3.2.0-59-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-59-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-58-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-58-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-58-generic ...'
	linux	/boot/vmlinuz-3.2.0-58-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-58-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-53-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-53-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-53-generic ...'
	linux	/boot/vmlinuz-3.2.0-53-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-53-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-51-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-51-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-51-generic ...'
	linux	/boot/vmlinuz-3.2.0-51-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-51-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux	/boot/vmlinuz-3.2.0-37-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-37-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	echo	'Loading Linux 3.2.0-37-generic ...'
	linux	/boot/vmlinuz-3.2.0-37-generic root=UUID=c829136a-7740-4a11-837e-aa5797607acc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-37-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root c829136a-7740-4a11-837e-aa5797607acc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c829136a-7740-4a11-837e-aa5797607acc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cdb2c20e-cf52-4bff-90e4-84dd09002c29 none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda1/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sda1: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

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

menuentry "Start Kubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/kubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Start Kubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity  quiet splash --

label ubnentry2
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry3
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry4
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry5
menu label Start Kubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --

label ubnentry6
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/kubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry7
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
cat: /tmp/BootInfo-SrvwuQRW/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-SrvwuQRW/Tmp_Log: No such file or directory
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-SrvwuQRW/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-SrvwuQRW/Tmp_Log: No such file or directory
  No volume groups found
```


 how i can make actions on it to solve this kernel panic error?

Thank you for suggestions.
Regards

---

### Post by Esilvanio on 2014-09-03
ok i have solved it, i have maden some tips and then installed grub again in right partion, i have done correctly all and now all is as before..even better then before.
Bye

---

