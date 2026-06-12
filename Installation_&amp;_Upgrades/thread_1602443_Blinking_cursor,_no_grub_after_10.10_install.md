---
title: "Blinking cursor, no grub after 10.10 install"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by tredmer on 2010-10-21
I decided to swap my media center PC over to Kubuntu after I had some issues with the Ubuntu 10.04 to 10.10 update. It has had Ubuntu on it for probably 3 years now. Most notably, the same issue is occuring now with any installer later than 9.04 which leads me to believe it is all Grub2 related.

The install runs without errors, but after booting from HD I get only a blinking insertion cursor. No Grub at all. I've held in shift, nada. I booted to Live CD and reinstalled Grub manually but still no love. It acts as though Grub simply isn't there.

I do have a second hard drive in the box that has Ubuntu 9.04 on it that I use as a backup if the OS HD gets messed up, but it is second in boot order and shouldn't be causing an issue. Besides, if that HD was booting it would be giving me legacy grub, not a blinking cursor.

Any thoughts? I am pulling my hair out.

---

### Post by sikander3786 on 2010-10-21
Are you sure you installed Grub to the MBR of the HDD you intended to boot off?

It would be better to post the output of bootinfoscript as it would make it a lot easier to diagnose the problem. Script and instructions here.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please wrap the output with proper code tags #.

---

### Post by tredmer on 2010-10-21
I'll follow the link once I get home to the computer, but I didn't do anything other than run the installer, which has never given me trouble in the past. I selected the drive (sdb) during installation.

EDIT: Just ran the script on my office computer (shhhh don't tell IT) and wow, would have been very handy to have yesterday. Thanks!

---

### Post by tredmer on 2010-10-21
Ok, ran the script and seem to have found the problem. I'm going to try and install the Grub on sdb, not sure why it didn't install there by default since that was the drive I installed it on...

Any insight on the easiest way to manually install Grub2 on a drive would be appreciated.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   970,759,754   970,759,692  83 Linux
/dev/sda2         970,759,755   976,768,064     6,008,310   5 Extended
/dev/sda5         970,759,818   976,768,064     6,008,247  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   150,155,263   150,153,216  83 Linux
/dev/sdb2         150,157,310   156,301,311     6,144,002   5 Extended
/dev/sdb5         150,157,312   156,301,311     6,144,000  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9ee5da8e-e9af-4421-9e95-3a3dc08ec246   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a85266a0-c7bb-43e9-b921-2cad1b032fe2   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c25c546e-5b40-46f0-92a2-6fba4273c5a8   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        cb091bae-04fe-43a2-b218-93c0a78a5f32   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=9ee5da8e-e9af-4421-9e95-3a3dc08ec246 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a85266a0-c7bb-43e9-b921-2cad1b032fe2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .6GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: vmlinuz

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
search --no-floppy --fs-uuid --set c25c546e-5b40-46f0-92a2-6fba4273c5a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c25c546e-5b40-46f0-92a2-6fba4273c5a8
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set c25c546e-5b40-46f0-92a2-6fba4273c5a8
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c25c546e-5b40-46f0-92a2-6fba4273c5a8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set c25c546e-5b40-46f0-92a2-6fba4273c5a8
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c25c546e-5b40-46f0-92a2-6fba4273c5a8 ro single 
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
	search --no-floppy --fs-uuid --set c25c546e-5b40-46f0-92a2-6fba4273c5a8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set c25c546e-5b40-46f0-92a2-6fba4273c5a8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10 (9.10) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 9ee5da8e-e9af-4421-9e95-3a3dc08ec246
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=c25c546e-5b40-46f0-92a2-6fba4273c5a8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cb091bae-04fe-43a2-b218-93c0a78a5f32 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  15.1GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
  15.1GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
  15.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  f6 68 d6 dc 67 85 b4 d0  d1 a7 37 b9 e5 fa 81 69  |.h..g.....7....i|
00000010  ec c3 8b 78 3f 2d 8e aa  0c 96 c3 cb aa 19 a2 4a  |...x?-.........J|
00000020  3c d4 5c f4 19 f5 04 a0  6e 68 80 d4 61 52 37 c4  |<.\.....nh..aR7.|
00000030  d3 c2 c7 fd c2 5d c1 67  0e 69 85 59 1a df 11 e2  |.....].g.i.Y....|
00000040  61 66 41 6c af d9 33 63  01 e6 70 e0 c5 20 5d 97  |afAl..3c..p.. ].|
00000050  00 7c 45 80 1a 37 45 2d  b9 e8 96 10 44 63 ba 7e  |.|E..7E-....Dc.~|
00000060  52 9f 36 04 5f 2e f9 9d  5a fe ba 1c 7d a6 8f 7d  |R.6._...Z...}..}|
00000070  e4 1c 60 f8 0d 47 a6 39  64 c1 21 3f 5c a6 99 41  |..`..G.9d.!?\..A|
00000080  5a 67 ba 7f a0 26 c9 5f  be 0f db cd 8d 45 4c 63  |Zg...&._.....ELc|
00000090  07 35 88 d1 78 ec d5 ff  4e e1 d2 b5 94 4c 58 c9  |.5..x...N....LX.|
000000a0  61 be 03 bc 69 98 94 8b  df ab dc d1 09 ff b4 34  |a...i..........4|
000000b0  69 df f7 db 65 94 80 12  bb 1a 2f 90 f6 a3 ff c2  |i...e...../.....|
000000c0  4c df 0f d3 2e 9e 80 b1  8e 14 16 03 33 bc 72 99  |L...........3.r.|
000000d0  f2 1e 38 c4 d8 a4 09 e1  04 db f6 c3 4a 09 6c dc  |..8.........J.l.|
000000e0  eb 9c bd 7f df 9d 87 35  15 ba 28 a2 5b b3 f1 e1  |.......5..(.[...|
000000f0  6c d8 90 30 65 18 dd 1a  c0 54 81 0c 60 4f 35 05  |l..0e....T..`O5.|
00000100  3f f6 79 37 ad de df 53  1e c3 49 ac 5b d7 0f 99  |?.y7...S..I.[...|
00000110  3a be 05 18 4a 5e 17 86  42 35 a2 31 ec cc 00 fc  |:...J^..B5.1....|
00000120  45 c1 c5 18 1f c3 68 dc  a2 c5 c7 71 71 10 f7 bf  |E.....h....qq...|
00000130  fe d3 c7 f9 14 ea 27 76  7e 8b 0c 8a 07 3b d6 78  |......'v~....;.x|
00000140  9f 82 d3 23 ec 7e 8b 39  d4 20 be c1 c5 92 1a ea  |...#.~.9. ......|
00000150  16 25 5f 25 b5 21 88 88  f4 34 55 af 93 61 38 08  |.%_%.!...4U..a8.|
00000160  fa 10 16 6a 59 bd 6c e2  4b b5 5d 66 1c 9f 31 8c  |...jY.l.K.]f..1.|
00000170  de 48 72 b1 8a a3 0c fc  23 a2 77 3b 73 58 49 27  |.Hr.....#.w;sXI'|
00000180  73 0d 66 05 b8 1d 81 95  f5 33 e8 a1 d7 ca 9c c0  |s.f......3......|
00000190  99 6b e5 dc 4f c4 ff 2f  bf 9f 02 41 21 ef 64 12  |.k..O../...A!.d.|
000001a0  40 31 c5 a4 42 f4 af b7  b6 3e 43 20 bb 34 59 ed  |@1..B....>C .4Y.|
000001b0  9f 49 f2 e1 d2 2c e4 53  c5 ea 38 bb 0d d9 00 fe  |.I...,.S..8.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c0 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by tredmer on 2010-10-21
Got it! Thank you immensely for that script, once I ran it I knew what the problem was.

Booted from the LiveCD then ran:

```
sudo mmount /dev/sdb1 /mnt
```

That mounted the drive I wanted to boot from, then:

```
sudo grub-install --root-directory=/mnt /dev/sdb
```

That installed GRUB2 on the correct partition from the LiveCD and the rest was booting history. Hope that helps someone else, thanks again.

---

