---
title: "Copying distro to another drive"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by JohnMac on 2011-05-29
I have a plug IDE drive the same size as my normal HDD and I tried to make a bootable copy using dd so I can be ready should my new Natty instal fails.
The copy HDD will boot as long as the normal HDD is there, but won't boot if I disconnect the main HDD. I get: error: out of disk. grub rescue. I cannot make any sense of my grib menu either.

My Boot Info Script (can't recall how to attach it) does show something not right with my Boot Sector info - "core.img cannot be found at this location"

My system: Desktop AMD Dual 5200 CPU, 2G RAM, Geforce N439GT graphics.
HDD: SATA 160G and IDE 160G removable.
Distro: Maverick

Any Hints?

---

### Post by nitstorm on 2011-05-29
Good idea would be to post the output of the Boot Info Script here. Also it seems like there is no grub installed on the Plug IDE HDD (if i am saying it right :P  )

---

### Post by JohnMac on 2011-05-30
I think I did try to install grub onto my IDE drive from the livecd without success, but anyway check this out:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 277097296 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   300,503,039   300,500,992  83 Linux
/dev/sda2         300,505,086   312,580,095    12,075,010   5 Extended
/dev/sda5         300,505,088   312,580,095    12,075,008  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 130 MB, 130940928 bytes
16 heads, 32 sectors/track, 499 cylinders, total 255744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32       255,486       255,455   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e6ba8339-16bb-4335-b6bb-ea552e87c08e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        36b9fb7d-a0b7-477c-937b-2358d7fa1b26   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5447-4D31                              vfat       REMOVABLE                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/REMOVABLE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
set locale_dir=($root)/boot/grub/locale
set lang=en
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
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
# Commented out by Dropbox
# UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5504bb90-c234-4087-bb2c-4a498392dcf9 none            swap    sw              0       0
UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e / ext4 errors=remount-ro,user_xattr 0 1

=================== sda1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
  60.6GB: boot/grub/grub.cfg
 125.3GB: boot/initrd.img-2.6.35-22-generic
 125.3GB: boot/initrd.img-2.6.35-25-generic
    .7GB: boot/initrd.img-2.6.35-27-generic
   3.1GB: boot/initrd.img-2.6.35-28-generic
 142.0GB: boot/vmlinuz-2.6.35-22-generic
 142.0GB: boot/vmlinuz-2.6.35-25-generic
 142.0GB: boot/vmlinuz-2.6.35-27-generic
 142.1GB: boot/vmlinuz-2.6.35-28-generic
   3.1GB: initrd.img
    .7GB: initrd.img.old
 142.1GB: vmlinuz
 142.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c1 93 dd b4 c2 d9 e9 a8  34 92 24 c9 eb da 18 ba  |........4.$.....|
00000010  1c 1d 6a 8b 92 d0 8d 97  00 0f 2c cd 29 73 63 d8  |..j.......,.)sc.|
00000020  ad 9f b6 71 35 f2 ad 11  5c b6 0b 0b 6b ad 88 8c  |...q5...\...k...|
00000030  ac e6 90 ac d5 c9 a6 f6  8c b2 60 63 8c e6 94 63  |..........`c...c|
00000040  da 33 ab a6 d1 aa b5 1b  15 ad 5a 5a d6 96 0d 93  |.3........ZZ....|
00000050  8b 15 c1 6a b0 6c 58 39  03 6d 13 e6 27 d6 d6 6c  |...j.lX9.m..'..l|
00000060  d5 86 3d b2 22 1a 6b b4  d1 68 c3 30 a1 41 1a 97  |..=.".k..h.0.A..|
00000070  c8 d8 30 6c 56 46 84 91  cc 59 1e 68 1b e8 03 47  |..0lVF...Y.h...G|
00000080  66 41 0d e3 b6 50 02 58  61 c9 5f 66 14 e6 80 43  |fA...P.Xa._f...C|
00000090  61 0a d4 e0 f3 66 b4 b2  08 19 4a 8b 08 74 1c 6c  |a....f....J..t.l|
000000a0  bc 61 b2 25 51 a1 97 bf  96 3a 0d 2c 0c e7 dc 1a  |.a.%Q....:.,....|
000000b0  5a 8c 6e 0a d8 2c b5 f4  e7 56 24 74 87 81 f4 3b  |Z.n..,...V$t...;|
000000c0  90 b2 94 33 19 d8 90 0d  00 00 58 03 7f 13 07 01  |...3......X.....|
000000d0  f4 a6 b4 10 77 4f fd bf  79 6b 38 96 ff 97 de aa  |....wO..yk8.....|
000000e0  1e fe 0b 41 12 13 e2 50  b5 ad d5 1e 05 7a fa 2a  |...A...P.....z.*|
000000f0  5a 55 9b b5 3d f0 90 5b  68 c0 b4 ad 4d 6d f6 ff  |ZU..=..[h...Mm..|
00000100  4b 42 bd 92 ac c1 13 2d  d3 ef c0 b7 79 14 b2 19  |KB.....-....y...|
00000110  b3 1a 40 47 18 44 52 6d  74 00 28 c4 a5 b4 2d c5  |..@G.DRmt.(...-.|
00000120  56 03 e2 9d 03 90 50 13  0c 60 b1 e6 a0 f6 59 c2  |V.....P..`....Y.|
00000130  15 fb 7f 30 66 6a 2b 19  1c e8 03 47 20 42 0b a3  |...0fj+....G B..|
00000140  ed 66 cd 07 ec ff d9 80  b5 b5 32 16 bb cb 5b b5  |.f........2...[.|
00000150  0f 3e 09 0a 99 ab 39 09  21 1d 0d 6c 4a 5b ac 25  |.>....9.!..lJ[.%|
00000160  35 38 0d 92 75 a2 1a 43  27 f8 52 b1 00 91 4c a1  |58..u..C'.R...L.|
00000170  6d 84 21 d1 1b a0 4c a1  74 75 d1 b6 ef 66 63 60  |m.!...L.tu...fc`|
00000180  01 94 86 7c 9a 77 74 b3  81 bb 6d fd 36 a2 9b cd  |...|.wt...m.6...|
00000190  cb 2c 7d e5 9b 5b 42 3d  6e 4a a8 ef 22 9f 13 c1  |.,}..[B=nJ.."...|
000001a0  65 7b 30 d4 0f 73 17 f7  08 db 12 1e 9b d3 b1 39  |e{0..s.........9|
000001b0  f0 4c 2f 5e 10 f2 e3 6b  5e da 7e 80 1e f1 00 fe  |.L/^...k^.~.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 b8 00 00 00  |...........@....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by JohnMac on 2011-05-31
Oops that wasn't right, maybe I didn't have the drive plugged in that time.Try this for size:
```
       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 277097296 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   300,503,039   300,500,992  83 Linux
/dev/sda2         300,505,086   312,580,095    12,075,010   5 Extended
/dev/sda5         300,505,088   312,580,095    12,075,008  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   300,292,095   300,290,048  83 Linux
/dev/sdb2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sdb5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 130 MB, 130940928 bytes
16 heads, 32 sectors/track, 499 cylinders, total 255744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32       255,486       255,455   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e6ba8339-16bb-4335-b6bb-ea552e87c08e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        36b9fb7d-a0b7-477c-937b-2358d7fa1b26   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e6ba8339-16bb-4335-b6bb-ea552e87c08e   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5504bb90-c234-4087-bb2c-4a498392dcf9   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        5447-4D31                              vfat       REMOVABLE                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/REMOVABLE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
set locale_dir=($root)/boot/grub/locale
set lang=en
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single
	initrd /boot/initrd.img-2.6.35-22-generic
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
# Commented out by Dropbox
# UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5504bb90-c234-4087-bb2c-4a498392dcf9 none            swap    sw              0       0
UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e / ext4 errors=remount-ro,user_xattr 0 1

=================== sda1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
  61.3GB: boot/grub/grub.cfg
 125.3GB: boot/initrd.img-2.6.35-22-generic
 125.3GB: boot/initrd.img-2.6.35-25-generic
    .7GB: boot/initrd.img-2.6.35-27-generic
   3.1GB: boot/initrd.img-2.6.35-28-generic
 142.0GB: boot/vmlinuz-2.6.35-22-generic
 142.0GB: boot/vmlinuz-2.6.35-25-generic
 142.0GB: boot/vmlinuz-2.6.35-27-generic
 142.1GB: boot/vmlinuz-2.6.35-28-generic
   3.1GB: initrd.img
    .7GB: initrd.img.old
 142.1GB: vmlinuz
 142.0GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
set locale_dir=($root)/boot/grub/locale
set lang=en
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
# Commented out by Dropbox
# UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5504bb90-c234-4087-bb2c-4a498392dcf9 none            swap    sw              0       0
UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e / ext4 errors=remount-ro,user_xattr 0 1

=================== sdb1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
 142.2GB: boot/grub/grub.cfg
 125.3GB: boot/initrd.img-2.6.35-22-generic
 125.3GB: boot/initrd.img-2.6.35-25-generic
    .7GB: boot/initrd.img-2.6.35-27-generic
   3.1GB: boot/initrd.img-2.6.35-28-generic
 142.0GB: boot/vmlinuz-2.6.35-22-generic
 142.0GB: boot/vmlinuz-2.6.35-25-generic
 142.0GB: boot/vmlinuz-2.6.35-27-generic
 142.1GB: boot/vmlinuz-2.6.35-28-generic
   3.1GB: initrd.img
    .7GB: initrd.img.old
 142.1GB: vmlinuz
 142.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c1 93 dd b4 c2 d9 e9 a8  34 92 24 c9 eb da 18 ba  |........4.$.....|
00000010  1c 1d 6a 8b 92 d0 8d 97  00 0f 2c cd 29 73 63 d8  |..j.......,.)sc.|
00000020  ad 9f b6 71 35 f2 ad 11  5c b6 0b 0b 6b ad 88 8c  |...q5...\...k...|
00000030  ac e6 90 ac d5 c9 a6 f6  8c b2 60 63 8c e6 94 63  |..........`c...c|
00000040  da 33 ab a6 d1 aa b5 1b  15 ad 5a 5a d6 96 0d 93  |.3........ZZ....|
00000050  8b 15 c1 6a b0 6c 58 39  03 6d 13 e6 27 d6 d6 6c  |...j.lX9.m..'..l|
00000060  d5 86 3d b2 22 1a 6b b4  d1 68 c3 30 a1 41 1a 97  |..=.".k..h.0.A..|
00000070  c8 d8 30 6c 56 46 84 91  cc 59 1e 68 1b e8 03 47  |..0lVF...Y.h...G|
00000080  66 41 0d e3 b6 50 02 58  61 c9 5f 66 14 e6 80 43  |fA...P.Xa._f...C|
00000090  61 0a d4 e0 f3 66 b4 b2  08 19 4a 8b 08 74 1c 6c  |a....f....J..t.l|
000000a0  bc 61 b2 25 51 a1 97 bf  96 3a 0d 2c 0c e7 dc 1a  |.a.%Q....:.,....|
000000b0  5a 8c 6e 0a d8 2c b5 f4  e7 56 24 74 87 81 f4 3b  |Z.n..,...V$t...;|
000000c0  90 b2 94 33 19 d8 90 0d  00 00 58 03 7f 13 07 01  |...3......X.....|
000000d0  f4 a6 b4 10 77 4f fd bf  79 6b 38 96 ff 97 de aa  |....wO..yk8.....|
000000e0  1e fe 0b 41 12 13 e2 50  b5 ad d5 1e 05 7a fa 2a  |...A...P.....z.*|
000000f0  5a 55 9b b5 3d f0 90 5b  68 c0 b4 ad 4d 6d f6 ff  |ZU..=..[h...Mm..|
00000100  4b 42 bd 92 ac c1 13 2d  d3 ef c0 b7 79 14 b2 19  |KB.....-....y...|
00000110  b3 1a 40 47 18 44 52 6d  74 00 28 c4 a5 b4 2d c5  |..@G.DRmt.(...-.|
00000120  56 03 e2 9d 03 90 50 13  0c 60 b1 e6 a0 f6 59 c2  |V.....P..`....Y.|
00000130  15 fb 7f 30 66 6a 2b 19  1c e8 03 47 20 42 0b a3  |...0fj+....G B..|
00000140  ed 66 cd 07 ec ff d9 80  b5 b5 32 16 bb cb 5b b5  |.f........2...[.|
00000150  0f 3e 09 0a 99 ab 39 09  21 1d 0d 6c 4a 5b ac 25  |.>....9.!..lJ[.%|
00000160  35 38 0d 92 75 a2 1a 43  27 f8 52 b1 00 91 4c a1  |58..u..C'.R...L.|
00000170  6d 84 21 d1 1b a0 4c a1  74 75 d1 b6 ef 66 63 60  |m.!...L.tu...fc`|
00000180  01 94 86 7c 9a 77 74 b3  81 bb 6d fd 36 a2 9b cd  |...|.wt...m.6...|
00000190  cb 2c 7d e5 9b 5b 42 3d  6e 4a a8 ef 22 9f 13 c1  |.,}..[B=nJ.."...|
000001a0  65 7b 30 d4 0f 73 17 f7  08 db 12 1e 9b d3 b1 39  |e{0..s.........9|
000001b0  f0 4c 2f 5e 10 f2 e3 6b  5e da 7e 80 1e f1 00 fe  |.L/^...k^.~.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 b8 00 00 00  |...........@....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  77 ba 9e e2 34 05 a3 a5  1e e3 c0 f4 dc 58 7c ce  |w...4........X|.|
00000010  74 89 e9 b8 bb 70 dd e9  bd 6c e1 7b 02 2a 7b 5d  |t....p...l.{.*{]|
00000020  18 02 ca d4 ff aa b1 bd  7e 2a b6 d7 85 af e5 c2  |........~*......|
00000030  5e 3f ff 4b b2 57 b5 45  de a3 9a f3 83 a3 73 50  |^?.K.W.E......sP|
00000040  fc 89 98 28 b1 45 f6 a3  a8 4b 4c ad 71 d8 bf 74  |...(.E...KL.q..t|
00000050  54 c6 52 b3 15 bd ff f7  97 89 bd 06 ab 3a d5 ef  |T.R..........:..|
00000060  6f 0a 88 17 72 f7 0a 8e  3f 1d d3 5e 4c f1 f0 1d  |o...r...?..^L...|
00000070  0a 98 99 a3 72 15 a2 e7  3d 4e 3c a4 80 a7 11 d0  |....r...=N<.....|
00000080  f8 bd a1 f1 8c e0 16 84  0b 11 bd 47 41 fa 86 d5  |...........GA...|
00000090  03 93 f7 86 32 8b 13 ff  31 dc cc 7f ac 2e 05 43  |....2...1......C|
000000a0  3e f2 b2 8f fe 43 17 12  12 ee 1a f9 8f f2 77 bd  |>....C........w.|
000000b0  f8 8f bb 53 05 fa 9f 61  ec 3f 06 66 98 f8 8f 35  |...S...a.?.f...5|
000000c0  02 62 35 32 4c fc c7 b8  a9 b9 f0 1f bb a6 7a c9  |.b52L.........z.|
000000d0  6f 2a 09 9a df fe a7 79  7e b3 e0 4f b3 fc 26 65  |o*.....y~..O..&e|
000000e0  8a e0 fd af 3f cd f2 9b  95 53 72 93 df a4 4f 31  |....?....Sr...O1|
000000f0  cb 6f ba 09 5a bf e2 36  cf 6f 7e 74 9b e5 37 7e  |.o..Z..6.o~t..7~|
00000100  02 8a f3 dd 66 f9 cd 6f  93 73 e3 ed 6c 53 34 f9  |....f..o.s..lS4.|
00000110  8d 42 0b 1f 01 fa 70 b2  be f5 62 8c 9f 10 03 7e  |.B....p...b....~|
00000120  ee ba e4 de c1 5a 19 47  b1 b6 80 e2 01 05 e3 88  |.....Z.G........|
00000130  1e 23 67 92 09 3f ba c0  dc 62 b2 ec bd c7 41 ae  |.#g..?...b....A.|
00000140  35 81 fc 9f 28 fe 97 c0  f8 7f f1 b9 e3 ff 9f 86  |5...(...........|
00000150  f1 ff 4f 6f f1 7f 92 20  fe df 36 89 ff b7 cd e2  |..Oo... ..6.....|
00000160  7f ac 20 fe df 36 8b ff  b1 b9 89 ff b1 5e ec 77  |.. ..6.......^.w|
00000170  b0 a0 f9 bb b7 cc ed f7  b7 5b 66 f6 6b 13 50 5c  |.........[f.k.P\|
00000180  7e cb cc 7e af c4 e4 c6  7e 2b c4 9a d9 ef a7 31  |~..~....~+.....1|
00000190  fa d6 cb dd 32 b7 df 9c  9b 66 f6 db 42 40 f1 e4  |....2....f..B@..|
000001a0  4d 33 fb 2d 16 93 1b fb  ed 12 23 eb 7b 0b c8 56  |M3.-......#.{..V|
000001b0  e0 38 08 ff 3e de 03 2b  ee ff 3a c7 e5 27 00 fe  |.8..>..+..:..'..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by JohnMac on 2011-06-30
Sorry - I didn,t say my problem was resolved. I cannot get my copied drive to boot!!

---

### Post by Herman on 2011-06-30
> I have a plug IDE drive the same size as my normal HDD ... 
Okay, I'll bite.

This could be embarrassing, but I have never heard of a '*plug* IDE drive' before. :redface:

Can you explain more about what you mean by the term '*plug* IDE drive'? 
How is your '*plug*' IDE drive different from a 'normal' IDE drive?

---

### Post by YesWeCan on 2011-06-30
Well you have some peculiarities here. First, Grub has been installed to the partition and also to the MBR. Presumably the core.img file in the MBR area of the clone is looking on the original disk for the rest of Grub.

[edit - sorry, messed up]
Connect the clone and boot off the original again. Run
[COLOR="Navy"]sudo update-grub[/COLOR]
To add the cloned Ubuntu to the menu. Reboot and choose the cloned Ubuntu and boot into it. Run
[COLOR="Navy"]sudo fdisk -l[/COLOR] to confirm the clone drive is still called sdb and then run
[COLOR="Navy"]sudo grub-install /dev/sdb[/COLOR]
You should now be able to disconnect the original and boot the clone.

---

### Post by dFlyer on 2011-06-30
> **Herman said:**
> Okay, I'll bite.

This could be embarrassing, but I have never heard of a '*plug* IDE drive' before. :redface:

Can you explain more about what you mean by the term '*plug* IDE drive'? 
How is your '*plug*' IDE drive different from a 'normal' IDE drive?

I have a usb cable that allow a person to use an ide or sata drive as an external had. Works great for backs, cloning and photo storage.

---

### Post by Herman on 2011-06-30
> I have a usb cable that allow a person to use an ide or sata drive as an  external had. Works great for backs, cloning and photo storage.Oh, I just call that a plain ordinary USB external drive. (LOL) 
I have SATA and IDE external drives and when I need a USB to IDE or USB to SATA adapter I just pull the end out ot one of my USB external enclosures and use it for an adapter. If it's going to be for long I even put the hard drive inside the box and fasten the holding screws.
 I guess it's because I live several hours away from town, so I tend to improvise rather than think of going to a store and buying a special item just for a given job.

Thanks for the info.  :)

@johnmac,
By the way, if you ever intend to try booting while both drives are plugged in to the same motherboard, you will need, (or at least you should) to change your file system UUID for at least one copy.
Some cloning software, and GParted will do that for you, but if it isn't done it can lead to confusion about which file system contains the kernel to load and which holds the /sbin/init, (the / file system), since those are specified by their UUIDs now in GRUB.

The command 'sudo tune2fs -U random /dev/<insert device designation here>' can be used to change a file system's UUID.
Then you need to edit the operating system's /etc/fstab accordingly as well.
You also need to update your grub.cfg and check to make sure the correct UUIDs have been updated for each operating system.

If you don't perform those steps it will probably still boot okay, and I don't think it will do any immediate harm it just won't be technically correct, that's all.  :)

---

### Post by JohnMac on 2011-07-02
@ Herman

re: Plug-in IDE drive. I have a housing that fits into a CDROM slot in my desktop and plugs into an IDE connector. My 160g hard drive fits into the removable carriage. Good to remove my distro to prevent accidental damage!

---

### Post by JohnMac on 2011-07-02
Sorry, that message should be for dFlyer.

I'll have to do some homework before I attempt to change my UUIDs or my FSTAB for that matter, but thanks anyway.

---

### Post by Herman on 2011-07-02
re: Plug-in IDE drive. I have a housing that fits into a CDROM slot in  my desktop and plugs into an IDE connector. My 160g hard drive fits into  the removable carriage.
Ah! Okay, Cool! I think a setup like that would be a great idea! Much better than a USB external drive, you'd have more speed because your computer will be working through a faster interface and less likelihood of the drive being moved while it's spinning. Cool! :smile:

UUID Numbers - 

Let's say we're working for a transport company and I give you paperwork to go out in the yard and find tractor number B76 and hitch trailer number TFL540 and go somewhere, you'd know what to do right?
That's something like what GRUB's grub.cfg file does when our PC is starting up, there's a line for what kernel to load and which file system to load as the '/' (or 'root') file system.
Here's a snippet from your grub.cfg lines for booting up your main operating system, I can tell because this stanza starts with the heading '### BEGIN /etc/grub.d/10_linux ###',
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
```In this case GRUB is being told to look in file system number  e6ba8339-16bb-4335-b6bb-ea552e87c08e for a kernel in, and in file system  e6ba8339-16bb-4335-b6bb-ea552e87c08e for the root file system, containing  /sbin/init files, (which contain further instructions for the rest of the  boot-up).

Further down in your grub.cfg, there are the entries made by the OS Prober which obviously is stated in the commented line, these lines are supposed to be for booting your plug drive operating system,
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e6ba8339-16bb-4335-b6bb-ea552e87c08e
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=e6ba8339-16bb-4335-b6bb-ea552e87c08e ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
```One problem is, right now as you can see, your two copies of your operating system both have the same UUID numbers. 
When GRUB is booting up and you have both drives plugged in, it could pick either drive to look for the kernel in, and either drive to mount as the root file system at boot time, which contains /sbin/init.
That won't hurt anything, but it's not clear to GRUB which kernel to load or which /sbin/init to tell the kernel to use for the root '/' file system, (with /sbin/init in it). 

To be correct, we should change the UUID number in one of your file systems to some randomly generated new UUID number and then update a few files with the changes to make sure both of your operating systems can be distinctly identified.
That will avoid any confusion when you have both drives plugged in at boot time.

---

### Post by Herman on 2011-07-02
Before you start, you should have some other way to boot your system up  because some of the things we're about to do could make one of your  operating systems temporarily unbootable, or at least unbootable in the  normal way if things go wrong.
Since you already have two copies of your operating system that shouldn't be too much of a problem, just make sure your motherboard has a BIOS boot menu and you know which key to tap during boot-up to get to your BIOS boot menu to select which hard disk to boot. Some computers don't support that but most do. Usually you tap your F12 key or the F8 key, in the early stages of booting, but it could be the Esc key or some other key. Some computers display a message after p.o.s.t to let you know which key to use to access the motherboard's boot menu.

Otherwise you should consider making yourself a grub rescue disk in advance, this command should make you an .iso file that you can burn to a CD and use for booting with if you need it,
```
grub-mkrescue --output=rescue.iso /boot/grub
```Make sure you burn it to disc as an .iso file and not as a data CD.
You'll only need that if your computer doesn't have a BIOS boot menu, but it could be a handy thing to have around in any case.

---

### Post by Herman on 2011-07-02
> I have a plug IDE drive the same size as my normal HDD and I tried to  make a bootable copy using dd so I can be ready should my new Natty  instal fails.
The copy HDD will boot as long as the normal HDD is there, but won't  boot if I disconnect the main HDD. I get: error: out of disk. grub  rescue. I cannot make any sense of my grib menu either.

My Boot Info Script (can't recall how to attach it) does show something  not right with my Boot Sector info - "core.img cannot be found at this  location"

My system: Desktop AMD Dual 5200 CPU, 2G RAM, Geforce N439GT graphics.
HDD: SATA 160G and IDE 160G removable.
Distro: Maverick

Any Hints?Actually, that's all you probably need to do if you only want to install Natty Narwhal over your fixed drive's Meerkat install. 

I was thinking of taking you through changing the UUID and editing /etc/fstab, but you would only need to do that if you wanted to *upgrade* your Meerakt to Narwhal, as opposed to *re-installing* with Narwhal, which means you'll be formatting your fixed drive's partitions anyway. On re-reading your original post, that shouldn't be necessary. You just need an extra way to boot in case the wrong root file system was mounted at the time you ran those other commands from YesWeCan.
Actually, since both file systems are mirror images of each other, YesWeCan's commands might even be enough already.

Have you tested to see if your plug drive boots without the internal fixed drive plugged in yet?

If you meant *upgrade *as opposed to *re-installing* let me know and if that's the case I can help you sort out your UUIDs, grub menu.cfg and /etc/fstab files. It's not really all that complicated, just a few relatively easy commands.

---

### Post by JohnMac on 2011-07-06
I have a LiveCD which I use as a rescue disc. I have no problems using bios to switch between drives, but my removeable drive will not boot, with or without the other drive connected. I just get an "out of disk" error. I've tried to reinstall grub and the MBR without success.

---

### Post by Herman on 2011-07-06
Have you checked to make sure the plug drive is being detected and listed okay in your BIOS?

---

### Post by JohnMac on 2011-07-07
Yes, both my drives are visible on bios, I can shuffle them and whatever. My distro on my internal drive will not boot sometimes if I play with the bios. I have to use my liveCD/gparted to "check" the partition and then it will boot.

I assumed that I should be able to grub-install from the livecd but no. I tried also CHROOTing from the livecd, the grub  is installed but it can't find my drive.

I suppose it might be time to toss my plugin drive.

---

### Post by Herman on 2011-07-10
Sorry for leaving you hanging here, I have been doing some traveling.

If your plug drive is a dd copy of your original hard drive and it is detected and listed in your BIOS then I can't think of any reason (as far as software is concerned), why it shouldn't boot when the other drive is removed. 

What kind of ribbon cable are you using, the older 40 conductor type that work best when the jumpers on the drives set as 'master' and 'slave', or the newer 80 conductor ribbons with a black plug for 'master' and the grey plug for 'slave'?

If you tried setting the jumpers as appropriate and plugging either drive into the same connector, (to rule out cabling and jumper setting problems), and one will boot while the other doesn't then it would tend to indicate that there's either a hardware or a software problem in the drive that won't boot.

Then further testing of the drive that won't boot would be required before deciding if the hard drive itself is faulty or not.

Just because I can't see a software problem doesn't rule out the possibility that is might still be a boot loader or other software problem. :)

---

### Post by JohnMac on 2011-07-13
@ YesWeCan  - I didn't ignore you, when I tried to sudo grub-install /dev/sda I get a message "no such file" or something

@ Herman - I have an 80 pin cable,only the DVD and cloned drive are on it. My original drive is SATA. Thus it shouldn't matter if the clone is connected to master or slave. I swapped with no effect. IDE drives are not cheap anymore, I'll have to scrounge one somewhere.
:(

---

