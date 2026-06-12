---
title: "Grub out of disk on single boot machine."
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by hcker2000 on 2012-05-04
Ok guys I went from 11.10 to 12.04 via upgrade. That brought me to the grub out of disk> prompt.

I said "oh well" and did a clean install of ubuntu 12.04 32bit and am still getting the same grub out of disk> prompt.

I have tried [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") and the instructions at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) in section 8.5 with no luck.

I'm installing to the 80 gig drive and need to make sure the raid disks dont get messed with as all my important data is on there.

Thanks in advance.

Here is my boot info.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdd: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sde: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   148,439,039   148,436,992  83 Linux
/dev/sda2         148,441,086   156,301,311     7,860,226   5 Extended
/dev/sda5         148,441,088   156,301,311     7,860,224  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/sdb1               1,024         2,047         1,024   0 Empty
/dev/sdb3               1,024         2,047         1,024   0 Empty


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        38adca0f-b96b-4732-8bb4-5292ade2d5a6   ext4       
/dev/sda5        8ed3cda4-aaa3-49f4-9aff-f692560fc7db   swap       
/dev/sdb         c0d1562c-c56a-d224-dc95-0017ef97e63b   linux_raid_member 
/dev/sdc         c0d1562c-c56a-d224-dc95-0017ef97e63b   linux_raid_member 
/dev/sdd         c0d1562c-c56a-d224-dc95-0017ef97e63b   linux_raid_member 
/dev/sde         c0d1562c-c56a-d224-dc95-0017ef97e63b   linux_raid_member 
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set=root 38adca0f-b96b-4732-8bb4-5292ade2d5a6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 38adca0f-b96b-4732-8bb4-5292ade2d5a6
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 38adca0f-b96b-4732-8bb4-5292ade2d5a6
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=38adca0f-b96b-4732-8bb4-5292ade2d5a6 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 38adca0f-b96b-4732-8bb4-5292ade2d5a6
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=38adca0f-b96b-4732-8bb4-5292ade2d5a6 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 38adca0f-b96b-4732-8bb4-5292ade2d5a6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 38adca0f-b96b-4732-8bb4-5292ade2d5a6
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
UUID=38adca0f-b96b-4732-8bb4-5292ade2d5a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8ed3cda4-aaa3-49f4-9aff-f692560fc7db none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              2
               =                vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1


Unknown BootLoader on sdb3



=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory

```

---

### Post by darkod on 2012-05-04
I don't know if it related to the out of disk error, but if sdb is in the array too you may already have a problem. Did you notice this in the results:

isk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 [COLOR=Red]Invalid MBR Signature found.[/COLOR] 
/dev/sdb1               1,024         2,047         1,024   0 Empty
 /dev/sdb3               1,024         2,047         1,024   0 Empty

---

### Post by hcker2000 on 2012-05-04
Even if some thing were to get messed up with one drive I can always rebuild that drive from the other three disks so long as they are not messed up. Not to mention I think raid would respect the mbr portion of the disks so even if some thing did happen to that area I'm not sure it would effect the raid.

I'm hoping some one can help with the out of disk. I'm also going to try unplugging the raid drives and just leave the 80 gig and dvd drive plugged in and see if it will boot and if not re-install with only those plugged in.

---

### Post by hcker2000 on 2012-05-04
A bump and a link to some more info for any one else running into this issue. So far nothing I have tried has worked so I'm going to run a disk check on the disk itself.

[http://www.dudek.org/blog/220](http://www.dudek.org/blog/220)

---

### Post by hcker2000 on 2012-05-05
I switched drives and re-installed and every thing works fine so some thing weird was going on with that 80 gig drive.

---

