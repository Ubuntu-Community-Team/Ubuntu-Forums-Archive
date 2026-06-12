---
title: "mint then lubuntu won't boot after fresh install"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by snaponit on 2012-05-30
I installed linux mint 12 LXDE on a Dell Inspiron 2650 using a USB flash drive (also had a broken cd drive, so had to load plop boot manager on a floppy to tell it to look at USB).

It loaded as long as I put the option acpi=off in the boot options.

Then I installed, restarted the laptop and it's just a black screen.

Then I installed lubuntu 12.04 without removing mint, restart still black screen.

**Thanks **for any help with this craziness. Forgive me if it's simple, I'm a bit new to Linux.

Here are the results from bootinfoscript:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 12 LXDE
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 1415272 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 1415272 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    21,220,633    21,218,586  83 Linux
/dev/sda2          21,221,374    39,069,695    17,848,322   5 Extended
/dev/sda5          38,025,216    39,069,695     1,044,480  82 Linux swap / Solaris
/dev/sda6          21,221,376    38,025,215    16,803,840  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2030 MB, 2030043136 bytes
255 heads, 63 sectors/track, 246 cylinders, total 3964928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     3,964,927     3,964,865   b W95 FAT32


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2122 MB, 2122579968 bytes
2 heads, 63 sectors/track, 32902 cylinders, total 4145664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             32     4,145,663     4,145,632   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        562defbf-a0f9-43a1-9480-2ac9e42304bc   ext4       
/dev/sda5        e9ae1ee8-41a0-4ccb-a2fd-acadf537ec99   swap       
/dev/sda6        6c36da6d-e2e2-4121-934e-6f44059ea8aa   ext4       
/dev/sdb1        7C92-16C1                              vfat       MYLINUXLIVE
/dev/sdc1        2816-4BA1                              vfat       MYLINUXLIVE
/dev/zram0       90736599-fccd-41c5-b5d4-baac53d3049e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/MYLINUXLIVE       vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


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
search --no-floppy --fs-uuid --set=root 562defbf-a0f9-43a1-9480-2ac9e42304bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 562defbf-a0f9-43a1-9480-2ac9e42304bc
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Linux Mint 12 LXDE, 3.0.0-12-generic (/dev/sda1)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 562defbf-a0f9-43a1-9480-2ac9e42304bc
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=562defbf-a0f9-43a1-9480-2ac9e42304bc ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Linux Mint 12 LXDE, 3.0.0-12-generic (/dev/sda1) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 562defbf-a0f9-43a1-9480-2ac9e42304bc
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=562defbf-a0f9-43a1-9480-2ac9e42304bc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 562defbf-a0f9-43a1-9480-2ac9e42304bc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 562defbf-a0f9-43a1-9480-2ac9e42304bc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
UUID=562defbf-a0f9-43a1-9480-2ac9e42304bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e9ae1ee8-41a0-4ccb-a2fd-acadf537ec99 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 6c36da6d-e2e2-4121-934e-6f44059ea8aa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 6c36da6d-e2e2-4121-934e-6f44059ea8aa
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 6c36da6d-e2e2-4121-934e-6f44059ea8aa
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=6c36da6d-e2e2-4121-934e-6f44059ea8aa ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 6c36da6d-e2e2-4121-934e-6f44059ea8aa
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=6c36da6d-e2e2-4121-934e-6f44059ea8aa ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 6c36da6d-e2e2-4121-934e-6f44059ea8aa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 6c36da6d-e2e2-4121-934e-6f44059ea8aa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 12 LXDE, 3.0.0-12-generic (/dev/sda1) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 562defbf-a0f9-43a1-9480-2ac9e42304bc
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=562defbf-a0f9-43a1-9480-2ac9e42304bc ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Linux Mint 12 LXDE, 3.0.0-12-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 562defbf-a0f9-43a1-9480-2ac9e42304bc
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=562defbf-a0f9-43a1-9480-2ac9e42304bc ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6c36da6d-e2e2-4121-934e-6f44059ea8aa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e9ae1ee8-41a0-4ccb-a2fd-acadf537ec99 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               3
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  af c3 02 5c 66 20 0f b6  7c 24 22 40 01 74 24 2a  |...\f ..|$"@.t$*|
00000010  1e c0 05 84 e4 02 60 60  01 85 00 4e 0b 60 3b c3  |......``...N.`;.|
00000020  17 00 31 10 48 80 34 1e  10 8b 5c 24 34 42 18 02  |..1.H.4...\$4B..|
00000030  8b 0c 20 8b 33 db 8a dd  40 21 78 80 20 fb 01 0f  |.. .3...@!x. ...|
00000040  84 b2 20 0a 66 3b 90 fe  0f 85 d2 00 01 f6 c2 20  |.. .f;......... |
00000050  02 46 e1 00 01 e0 0d 5c  33 c9 40 3b 0f 09 00 19  |.F.....\3.@;....|
00000060  6c 4a c0 15 6c 0f 84 09  01 01 0b 44 24 60 3b c1  |lJ..l......D$`;.|
00000070  0f 85 e2 0a 61 01 74 24  18 20 79 01 29 80 68 01  |....a.t$. y.).h.|
00000080  a1 7c 83 c6 02 83 c5 02  49 8c 48 89 20 03 c0 1c  |.|......I.H. ...|
00000090  10 89 8c c2 2c 02 89 a4  11 f9 85 ff 0f 84 1f 17  |....,...........|
000000a0  81 1d 03 02 21 17 10 c1  01 54 24 38 00 8b 74 24  |....!....T$8..t$|
000000b0  10 33 c9 8b 42 8a 08 00  0e 18 41 2c 66 8b 0a c1  |.3..B.....A,f...|
000000c0  2d a2 16 41 2d 4c 24 30  c1 2d e9 60 0a 20 20 23  |-..A-L$0.-.`.  #|
000000d0  c1 e9 8c c0 85 85 ff 1c  75 30 80 0f a1 0e 60 2e  |........u0....`.|
000000e0  84 df 03 04 00 00 40 02  1d 8d 4c 24 64 26 bf 01  |......@...L$d&..|
000000f0  61 00 1c 18 66 60 3a 64  20 08 00 89 bc a2 10 eb  |a...f`:d .......|
00000100  81 8d 44 14 24 68 61 02  68 60 02 44 24 10 26 c7  |..D.$ha.h`.D$.&.|
00000110  a3 10 a1 05 e9 62 21 8a  44 24 0a 5c 01 28 55 20  |.....b!.D$.\.(U |
00000120  02 f6 44 24 23 30 c0 0f  84 4a 40 01 20 13 38 8b  |..D$#0...J@. .8.|
00000130  92 46 c1 2f 85 b7 60 46  8b 4c a0 1e 02 84 22 0a  |.F./..`F.L....".|
00000140  33 db 33 d2 48 74 20 0b  48 0f 85 de 00 03 66 8b  |3.3.Ht .H.....f.|
00000150  00 51 02 8b 76 18 66 8b  09 40 33 c0 66 8b 46 04  |.Q..v.f..@3.f.F.|
00000160  a1 1b fe 01 e1 02 39 4e  06 76 06 83 c6 50 10 48  |......9N.v...P.H|
00000170  75 f4 61 02 ea 64 02 0f  04 85 e0 21 01 3b 56 0c  |u.a..d.....!.;V.|
00000180  0f 82 c2 d6 23 01 0e 0f  87 cc 20 01 40 0c 02 38  |....#..... .@..8|
00000190  62 08 08 8b 49 1c 8d 3c  2a c1 62 01 0a 61 07 ae  |b...I..<*.b..a..|
000001a0  e1 04 39 17 41 c0 09 c7  08 48 75 f5 41 02 9b 11  |..9.A....Hu.A...|
000001b0  43 02 0f 85 92 01 01 8b  4f 02 00 66 85 c9 00 fe  |C.......O..f....|
000001c0  ff ff 82 fe ff ff 02 68  00 01 00 f0 0f 00 00 fe  |.......h........|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 68 00 01 00 00  |...........h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected


```

---

### Post by snaponit on 2012-05-30
After manually holding the power button down, I pressed e to configure boot options. I found the correct place to add acpi=off (after splash).

Once desktop started I made it permanent from terminal:
```
sudo leafpad /etc/default/grub
```
change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

exit with save

then 
```
sudo update-grub
```

works now.

---

### Post by snaponit on 2012-06-01
I replaced:

acpi=off

with

acpi=enable pci=noacpi


Now I can see the battery! and fan isn't always on, and we'll see if shutdown works properly now.

---

