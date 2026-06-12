---
title: "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by jchan91 on 2012-12-12
Hi,

I am dual booting Windows 7 and Ubuntu 12.04 on a Sony Vaio svt13112fxs. I have very basic understanding of OS concepts, so any extra comments on what's going on would be appreciated!

Problem: When I am switching back from Windows to Ubuntu, I get the following:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I hard restart my laptop, and then I can successfully boot into Ubuntu with no errors.

It is consistently occurring when I go from Windows to Ubuntu.

Background: I repartitioned my hard drive and installed Ubuntu recently. However, after doing so, I was unable to boot into Windows because it appeared that grub could not find the MBR for Windows. So I made some changes in grub.d, and I could see the Windows option in the grub menu, and successfully booted into Windows.

Things that might help: When I restart my laptop from Ubuntu, the grub menu includes the additional Windows entry I added. When I am going from Windows to Ubuntu, it is not included.

I used bootinfoscript and got the following. There's a lot of info here, but I don't know what to look for:
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/mapper/isw_ebigbchgj_SSDSpace.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

isw_ebigbchgj_SSDSpace1: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,934,719    27,932,672  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,934,720    28,651,519       716,800   7 NTFS / exFAT / HPFS
/dev/sda3          28,651,520   567,169,023   538,517,504   7 NTFS / exFAT / HPFS
/dev/sda4         567,171,070   976,771,071   409,600,002   5 Extended
/dev/sda5         567,171,072   968,585,215   401,414,144  83 Linux
/dev/sda6         968,587,264   976,771,071     8,183,808  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    23,519,231    23,517,184  84 OS/2 hidden C: drive


Drive: isw_ebigbchgj_SSDSpace _____________________________________________________________________

Disk /dev/mapper/isw_ebigbchgj_SSDSpace: 12.0 GB, 12043026432 bytes
255 heads, 63 sectors/track, 1464 cylinders, total 23521536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_ebigbchgj_SSDSpace1              2,048    23,519,231    23,517,184  84 OS/2 hidden C: drive


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B6C67E5CC67E1D35                       ntfs       Recovery
/dev/sda2        DC26547A2654579A                       ntfs       System Reserved
/dev/sda3        924455D24455BA25                       ntfs       
/dev/sda5        69342838-841c-4cee-b460-a922920d4b61   ext4       
/dev/sda6        47a13924-9089-4d1d-aed7-bd27891cd923   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
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
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	linux	/boot/vmlinuz-3.2.0-34-generic root=UUID=69342838-841c-4cee-b460-a922920d4b61 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	echo	'Loading Linux 3.2.0-34-generic ...'
	linux	/boot/vmlinuz-3.2.0-34-generic root=UUID=69342838-841c-4cee-b460-a922920d4b61 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-34-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	linux	/boot/vmlinuz-3.2.0-32-generic root=UUID=69342838-841c-4cee-b460-a922920d4b61 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	echo	'Loading Linux 3.2.0-32-generic ...'
	linux	/boot/vmlinuz-3.2.0-32-generic root=UUID=69342838-841c-4cee-b460-a922920d4b61 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	linux	/boot/vmlinuz-3.2.0-30-generic root=UUID=69342838-841c-4cee-b460-a922920d4b61 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	echo	'Loading Linux 3.2.0-30-generic ...'
	linux	/boot/vmlinuz-3.2.0-30-generic root=UUID=69342838-841c-4cee-b460-a922920d4b61 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=69342838-841c-4cee-b460-a922920d4b61 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=69342838-841c-4cee-b460-a922920d4b61 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 69342838-841c-4cee-b460-a922920d4b61
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root B6C67E5CC67E1D35
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root DC26547A2654579A
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7" {
set root=(hd0,msdos2)
chainloader +1
}### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=69342838-841c-4cee-b460-a922920d4b61 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=47a13924-9089-4d1d-aed7-bd27891cd923 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 398.812503815 = 428.221665280  boot/grub/core.img                             1
 420.647369385 = 451.666673664  boot/grub/grub.cfg                             1
 271.891330719 = 291.941093376  boot/initrd.img-3.2.0-29-generic               1
 419.578838348 = 450.519347200  boot/initrd.img-3.2.0-30-generic               2
 420.203838348 = 451.190435840  boot/initrd.img-3.2.0-32-generic               2
 420.828842163 = 451.861528576  boot/initrd.img-3.2.0-34-generic               2
 454.581764221 = 488.103452672  boot/vmlinuz-3.2.0-29-generic                  1
 272.593490601 = 292.695031808  boot/vmlinuz-3.2.0-30-generic                  1
 419.550525665 = 450.488946688  boot/vmlinuz-3.2.0-32-generic                  1
 419.945056915 = 450.912571392  boot/vmlinuz-3.2.0-34-generic                  2
 420.828842163 = 451.861528576  initrd.img                                     2
 420.203838348 = 451.190435840  initrd.img.old                                 2
 419.945056915 = 450.912571392  vmlinuz                                        2
 419.550525665 = 450.488946688  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  dd 8e 49 45 0c e3 38 02  38 00 00 00 00 00 00 00  |..IE..8.8.......|
00000010  00 00 00 00 00 00 00 00  04 7f 00 00 00 00 00 00  |................|
00000020  00 80 00 00 00 00 03 00  00 00 00 a8 00 00 00 00  |................|
00000030  00 00 00 00 3d bb 1a b1  4b e0 ff 80 5f f9 f7 dc  |....=...K..._...|
00000040  ff f3 ff 1f f6 0d f0 e2  e1 ff b1 67 ff b5 fd 89  |...........g....|
00000050  ff b0 de fe df f3 f6 08  5c 67 c3 e9 fa e5 a8 db  |........\g......|
00000060  4f 6b 6e ac f5 64 ef 9e  c6 98 fd 8d f7 bf 5f 2e  |Okn..d........_.|
00000070  be 4a 11 8d 7f df d7 d9  bf 4b 09 8c fc f7 d7 cd  |.J.......K......|
00000080  b7 41 36 2f 7c 5a 3a f1  db 93 f2 fa fe 7e 8f 73  |.A6/|Z:......~.s|
00000090  8b 05 b6 ba 79 3b 0f ef  cb c9 ee d9 7c b9 75 d5  |....y;......|.u.|
000000a0  5f 98 dd 3b da df 5f 7f  ef fc c7 ba ea 6e 73 1f  |_..;.._......ns.|
000000b0  db bb ec ea 9a b2 7a d5  cb f9 ca 9f b9 b6 d2 d8  |......z.........|
000000c0  fb 62 28 fd 18 5a a7 7e  cf f3 65 59 bd e9 5d e7  |.b(..Z.~..eY..].|
000000d0  fd 9a ba ee 76 f3 6f 77  85 8d 46 df be 3f 9d ff  |....v.ow..F..?..|
000000e0  ff 8e ee e5 77 bb f5 ef  7c a2 e4 bb ff ae d5 df  |....w...|.......|
000000f0  6f 63 bf 21 ac 66 7e be  0f 01 f7 8c bf 47 7f 1f  |oc.!.f~......G..|
00000100  45 eb 47 c3 fd de bd ff  fa f8 f7 df 75 7f fb fd  |E.G.........u...|
00000110  cf d2 ba f9 ff 3e 6b b5  5d 9a cb e5 ea fd 3f bb  |.....>k.].....?.|
00000120  de b7 ff e7 65 ff f4 f3  8c d6 fd ff fd fc 7c fa  |....e.........|.|
00000130  d9 dc ff df fd 57 8c bc  df 46 ef db c7 77 87 9f  |.....W...F...w..|
00000140  0e ca e5 24 56 ed 3e 0b  96 02 2d 3d b8 fe 1a b4  |...$V.>...-=....|
00000150  f3 d3 e7 5b d6 32 bf 77  d1 ef 6a f4 b3 bf d1 1f  |...[.2.w..j.....|
00000160  be db a4 58 fe 86 1e ba  ed 93 c5 79 9a 16 12 1d  |...X.......y....|
00000170  a3 57 eb ea 7f ef 15 be  e3 86 86 20 f8 05 9e 7d  |.W......... ...}|
00000180  81 00 60 80 01 0b d8 b9  c1 77 e7 90 de f7 dd fe  |..`......w......|
00000190  6e fb ee af fe 3a d9 bf  a5 e8 36 4f ce f3 ef fd  |n....:....6O....|
000001a0  97 e2 04 40 ba bd db bf  be fb 60 9d ee ff 47 fa  |...@......`...G.|
000001b0  ff 5a fc 3d b2 ff ff b7  4e da 9d ec ff fe 2f f5  |.Z.=....N...../.|
000001c0  37 75 7a 68 d4 f9 fb f7  eb c3 fa be 9d db af 18  |7uzh............|
000001d0  fd cb 6f 36 bb e7 eb da  ba c9 9b f9 f6 ef 8f b6  |..o6............|
000001e0  67 d6 3b f5 ff 3f ee 3b  b5 e7 0d f8 cf bf ed 9f  |g.;..?.;........|
000001f0  c1 c1 03 c5 ff d7 ff be  af d4 35 8c da df 5e be  |..........5...^.|
00000200

Unknown BootLoader on isw_ebigbchgj_SSDSpace1

00000000  dd 8e 49 45 0c e3 38 02  38 00 00 00 00 00 00 00  |..IE..8.8.......|
00000010  00 00 00 00 00 00 00 00  04 7f 00 00 00 00 00 00  |................|
00000020  00 80 00 00 00 00 03 00  00 00 00 a8 00 00 00 00  |................|
00000030  00 00 00 00 3d bb 1a b1  4b e0 ff 80 5f f9 f7 dc  |....=...K..._...|
00000040  ff f3 ff 1f f6 0d f0 e2  e1 ff b1 67 ff b5 fd 89  |...........g....|
00000050  ff b0 de fe df f3 f6 08  5c 67 c3 e9 fa e5 a8 db  |........\g......|
00000060  4f 6b 6e ac f5 64 ef 9e  c6 98 fd 8d f7 bf 5f 2e  |Okn..d........_.|
00000070  be 4a 11 8d 7f df d7 d9  bf 4b 09 8c fc f7 d7 cd  |.J.......K......|
00000080  b7 41 36 2f 7c 5a 3a f1  db 93 f2 fa fe 7e 8f 73  |.A6/|Z:......~.s|
00000090  8b 05 b6 ba 79 3b 0f ef  cb c9 ee d9 7c b9 75 d5  |....y;......|.u.|
000000a0  5f 98 dd 3b da df 5f 7f  ef fc c7 ba ea 6e 73 1f  |_..;.._......ns.|
000000b0  db bb ec ea 9a b2 7a d5  cb f9 ca 9f b9 b6 d2 d8  |......z.........|
000000c0  fb 62 28 fd 18 5a a7 7e  cf f3 65 59 bd e9 5d e7  |.b(..Z.~..eY..].|
000000d0  fd 9a ba ee 76 f3 6f 77  85 8d 46 df be 3f 9d ff  |....v.ow..F..?..|
000000e0  ff 8e ee e5 77 bb f5 ef  7c a2 e4 bb ff ae d5 df  |....w...|.......|
000000f0  6f 63 bf 21 ac 66 7e be  0f 01 f7 8c bf 47 7f 1f  |oc.!.f~......G..|
00000100  45 eb 47 c3 fd de bd ff  fa f8 f7 df 75 7f fb fd  |E.G.........u...|
00000110  cf d2 ba f9 ff 3e 6b b5  5d 9a cb e5 ea fd 3f bb  |.....>k.].....?.|
00000120  de b7 ff e7 65 ff f4 f3  8c d6 fd ff fd fc 7c fa  |....e.........|.|
00000130  d9 dc ff df fd 57 8c bc  df 46 ef db c7 77 87 9f  |.....W...F...w..|
00000140  0e ca e5 24 56 ed 3e 0b  96 02 2d 3d b8 fe 1a b4  |...$V.>...-=....|
00000150  f3 d3 e7 5b d6 32 bf 77  d1 ef 6a f4 b3 bf d1 1f  |...[.2.w..j.....|
00000160  be db a4 58 fe 86 1e ba  ed 93 c5 79 9a 16 12 1d  |...X.......y....|
00000170  a3 57 eb ea 7f ef 15 be  e3 86 86 20 f8 05 9e 7d  |.W......... ...}|
00000180  81 00 60 80 01 0b d8 b9  c1 77 e7 90 de f7 dd fe  |..`......w......|
00000190  6e fb ee af fe 3a d9 bf  a5 e8 36 4f ce f3 ef fd  |n....:....6O....|
000001a0  97 e2 04 40 ba bd db bf  be fb 60 9d ee ff 47 fa  |...@......`...G.|
000001b0  ff 5a fc 3d b2 ff ff b7  4e da 9d ec ff fe 2f f5  |.Z.=....N...../.|
000001c0  37 75 7a 68 d4 f9 fb f7  eb c3 fa be 9d db af 18  |7uzh............|
000001d0  fd cb 6f 36 bb e7 eb da  ba c9 9b f9 f6 ef 8f b6  |..o6............|
000001e0  67 d6 3b f5 ff 3f ee 3b  b5 e7 0d f8 cf bf ed 9f  |g.;..?.;........|
000001f0  c1 c1 03 c5 ff d7 ff be  af d4 35 8c da df 5e be  |..........5...^.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

---

