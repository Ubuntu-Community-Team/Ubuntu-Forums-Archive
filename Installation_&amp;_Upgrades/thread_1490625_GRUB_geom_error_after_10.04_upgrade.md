---
title: "GRUB geom error after 10.04 upgrade"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by el_manaba on 2010-05-22
Please help a Newbie out.

I upgraded from 9.10 to 10.04.  Previously, I had a dual booting system where GRUB allowed me to boot 9.10 or WinXP.  I have two hard drives - an 80 GB drive with XP and a 1 TB drive with Ubuntu.

During the upgrade I chose to upgrade my GRUB version.  I only selected to install grub on the Ubuntu drive.  I didn't work - I couldn't even get GRUB to load.  It just gave the error: the symbol 'grub_puts_' not found.

So I reconfigured GRUB and installed it on both drives.  Now GRUB loads and I can boot 10.04 just fine, but I can no longer boot XP.

What command should I run to give you a glimpse of my system?  Would that help diagnose this?

Thanks!

---

### Post by el_manaba on 2010-05-29
I found the Boot Info Script but I need a little help interpreting the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1288499914 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   156,280,319   115,314,570   f W95 Ext d (LBA)
/dev/sda5          40,965,813   156,280,319   115,314,507   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,250,275,823 1,250,275,761   7 HPFS/NTFS
/dev/sdb2       1,250,290,755 1,953,520,064   703,229,310   5 Extended
/dev/sdb5       1,250,290,818 1,938,402,899   688,112,082  83 Linux
/dev/sdb6       1,938,402,963 1,953,520,064    15,117,102  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        621072CB1072A5A7                       ntfs       Program                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2498B8C398B89530                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        840C44430C44328A                       ntfs       SATA640                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        44a17491-30bf-4aa3-9669-ff334416aed5   ext4                                     
/dev/sdb6        968242b7-dce5-4972-91b7-de9ee20a472a   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=44a17491-30bf-4aa3-9669-ff334416aed5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=44a17491-30bf-4aa3-9669-ff334416aed5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=44a17491-30bf-4aa3-9669-ff334416aed5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	echo	'Loading Linux 2.6.31-17-generic ...'
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=44a17491-30bf-4aa3-9669-ff334416aed5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 621072cb1072a5a7
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=44a17491-30bf-4aa3-9669-ff334416aed5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=968242b7-dce5-4972-91b7-de9ee20a472a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 640.4GB: boot/grub/core.img
 656.1GB: boot/grub/grub.cfg
 641.8GB: boot/initrd.img-2.6.31-17-generic
 641.8GB: boot/initrd.img-2.6.32-22-generic
 640.7GB: boot/vmlinuz-2.6.31-17-generic
 641.2GB: boot/vmlinuz-2.6.32-22-generic
 641.8GB: initrd.img
 641.8GB: initrd.img.old
 641.2GB: vmlinuz
 640.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  05 81 d2 2b a8 05 b1 c0  34 a8 11 00 76 40 00 de  |...+....4...v@..|
00000010  a3 a6 f5 68 1e 39 43 77  c7 39 84 47 7c 22 bb 0b  |...h.9Cw.9.G|"..|
00000020  1e c4 fc ae cb 0e 0a a5  8a 01 1f 4b 13 b7 1c 04  |...........K....|
00000030  a8 4f 48 01 9d 11 59 90  7e 22 19 3f a5 8a a8 2e  |.OH...Y.~".?....|
00000040  88 c0 7b 30 0a a0 37 be  25 f7 40 12 89 64 37 26  |..{0..7.%.@..d7&|
00000050  96 50 0e 16 c4 a0 85 a1  d4 76 c7 9e e7 f8 84 90  |.P.......v......|
00000060  32 52 1f 40 30 01 80 08  40 cf e5 13 77 e8 39 3b  |2R.@0...@...w.9;|
00000070  37 27 24 8b e4 72 ae 89  89 41 e0 46 36 b6 74 8c  |7'$..r...A.F6.t.|
00000080  0c 0c 4e 12 cc 01 1f fb  45 8c 1f d0 8e 3b 8d 23  |..N.....E....;.#|
00000090  a1 09 40 04 35 44 94 54  14 be 5f dd 48 e7 0e dc  |..@.5D.T.._.H...|
000000a0  73 8b e7 05 48 48 41 fc  2c 78 7c 90 03 e0 d2 80  |s...HHA.,x|.....|
000000b0  52 4d c0 8e 06 04 b8 79  1c 2a 7e a6 fb 7c 03 dc  |RM.....y.*~..|..|
000000c0  ff 31 cc 93 f6 15 bb 0a  98 59 1a 88 c7 63 10 85  |.1.......Y...c..|
000000d0  f5 33 98 7f 34 c8 a5 17  b8 d7 61 e8 3e 92 92 5a  |.3..4.....a.>..Z|
000000e0  32 05 be 4e 2c 35 09 10  e8 2d 0f 84 bf 17 21 20  |2..N,5...-....! |
000000f0  5f 32 5b a1 6a 48 49 8c  71 79 25 28 fd d0 8c 90  |_2[.jHI.qy%(....|
00000100  1e de 4a d6 47 20 c3 8e  c4 f2 0d 11 c1 60 e6 00  |..J.G .......`..|
00000110  85 21 25 64 e0 9d d9 6c  06 e0 1d a1 ce 3a 01 89  |.!%d...l.....:..|
00000120  30 86 f8 94 9e 18 19 97  c6 fc a1 58 60 14 0c e7  |0..........X`...|
00000130  1d 82 1f ba c7 e8 06 21  89 42 fa 40 aa 32 77 ec  |.......!.B.@.2w.|
00000140  8c 18 1a c5 e0 15 bf 4e  0f 28 3a 00 7c 05 43 0b  |.......N.(:.|.C.|
00000150  6e c8 1c 47 d0 0c 4a 2f  31 84 f8 00 00 01 07 52  |n..G..J/1......R|
00000160  ef 30 a1 75 09 ae 06 00  1a 14 50 59 a0 72 61 33  |.0.u......PY.ra3|
00000170  d1 55 42 7e 86 83 00 56  00 3f 91 10 89 a9 c5 23  |.UB~...V.?.....#|
00000180  97 d8 66 27 b6 48 71 82  a8 88 08 03 18 05 43 49  |..f'.Hq.......CI|
00000190  a9 03 04 20 ce 5f 08 40  b1 27 f1 49 c7 01 a8 98  |... ._.@.'.I....|
000001a0  94 6c 87 71 83 ff f0 0c  00 34 26 93 40 42 18 51  |.l.q.....4&.@B.Q|
000001b0  7f 20 6a 5c 0b 20 7f fd  80 e2 f8 98 07 60 00 01  |. j\. .......`..|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 4b 8f df 06 00 00  |......?...K.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

It looks like GRUB is installed on sda1, where Windows is installed.  If this is the problem, how do I correct it?

---

### Post by bcbc on 2010-05-29
> **el_manaba said:**
> It looks like GRUB is installed on sda1, where Windows is installed.  If this is the problem, how do I correct it?

Yes, it's the problem. See [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by oleink on 2010-05-29
> **el_manaba said:**
> I found the Boot Info Script but I need a little help interpreting the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1288499914 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   156,280,319   115,314,570   f W95 Ext d (LBA)
/dev/sda5          40,965,813   156,280,319   115,314,507   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,250,275,823 1,250,275,761   7 HPFS/NTFS
/dev/sdb2       1,250,290,755 1,953,520,064   703,229,310   5 Extended
/dev/sdb5       1,250,290,818 1,938,402,899   688,112,082  83 Linux
/dev/sdb6       1,938,402,963 1,953,520,064    15,117,102  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        621072CB1072A5A7                       ntfs       Program                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2498B8C398B89530                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        840C44430C44328A                       ntfs       SATA640                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        44a17491-30bf-4aa3-9669-ff334416aed5   ext4                                     
/dev/sdb6        968242b7-dce5-4972-91b7-de9ee20a472a   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=44a17491-30bf-4aa3-9669-ff334416aed5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=44a17491-30bf-4aa3-9669-ff334416aed5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=44a17491-30bf-4aa3-9669-ff334416aed5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	echo	'Loading Linux 2.6.31-17-generic ...'
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=44a17491-30bf-4aa3-9669-ff334416aed5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 44a17491-30bf-4aa3-9669-ff334416aed5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 621072cb1072a5a7
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=44a17491-30bf-4aa3-9669-ff334416aed5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=968242b7-dce5-4972-91b7-de9ee20a472a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 640.4GB: boot/grub/core.img
 656.1GB: boot/grub/grub.cfg
 641.8GB: boot/initrd.img-2.6.31-17-generic
 641.8GB: boot/initrd.img-2.6.32-22-generic
 640.7GB: boot/vmlinuz-2.6.31-17-generic
 641.2GB: boot/vmlinuz-2.6.32-22-generic
 641.8GB: initrd.img
 641.8GB: initrd.img.old
 641.2GB: vmlinuz
 640.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  05 81 d2 2b a8 05 b1 c0  34 a8 11 00 76 40 00 de  |...+....4...v@..|
00000010  a3 a6 f5 68 1e 39 43 77  c7 39 84 47 7c 22 bb 0b  |...h.9Cw.9.G|"..|
00000020  1e c4 fc ae cb 0e 0a a5  8a 01 1f 4b 13 b7 1c 04  |...........K....|
00000030  a8 4f 48 01 9d 11 59 90  7e 22 19 3f a5 8a a8 2e  |.OH...Y.~".?....|
00000040  88 c0 7b 30 0a a0 37 be  25 f7 40 12 89 64 37 26  |..{0..7.%.@..d7&|
00000050  96 50 0e 16 c4 a0 85 a1  d4 76 c7 9e e7 f8 84 90  |.P.......v......|
00000060  32 52 1f 40 30 01 80 08  40 cf e5 13 77 e8 39 3b  |2R.@0...@...w.9;|
00000070  37 27 24 8b e4 72 ae 89  89 41 e0 46 36 b6 74 8c  |7'$..r...A.F6.t.|
00000080  0c 0c 4e 12 cc 01 1f fb  45 8c 1f d0 8e 3b 8d 23  |..N.....E....;.#|
00000090  a1 09 40 04 35 44 94 54  14 be 5f dd 48 e7 0e dc  |..@.5D.T.._.H...|
000000a0  73 8b e7 05 48 48 41 fc  2c 78 7c 90 03 e0 d2 80  |s...HHA.,x|.....|
000000b0  52 4d c0 8e 06 04 b8 79  1c 2a 7e a6 fb 7c 03 dc  |RM.....y.*~..|..|
000000c0  ff 31 cc 93 f6 15 bb 0a  98 59 1a 88 c7 63 10 85  |.1.......Y...c..|
000000d0  f5 33 98 7f 34 c8 a5 17  b8 d7 61 e8 3e 92 92 5a  |.3..4.....a.>..Z|
000000e0  32 05 be 4e 2c 35 09 10  e8 2d 0f 84 bf 17 21 20  |2..N,5...-....! |
000000f0  5f 32 5b a1 6a 48 49 8c  71 79 25 28 fd d0 8c 90  |_2[.jHI.qy%(....|
00000100  1e de 4a d6 47 20 c3 8e  c4 f2 0d 11 c1 60 e6 00  |..J.G .......`..|
00000110  85 21 25 64 e0 9d d9 6c  06 e0 1d a1 ce 3a 01 89  |.!%d...l.....:..|
00000120  30 86 f8 94 9e 18 19 97  c6 fc a1 58 60 14 0c e7  |0..........X`...|
00000130  1d 82 1f ba c7 e8 06 21  89 42 fa 40 aa 32 77 ec  |.......!.B.@.2w.|
00000140  8c 18 1a c5 e0 15 bf 4e  0f 28 3a 00 7c 05 43 0b  |.......N.(:.|.C.|
00000150  6e c8 1c 47 d0 0c 4a 2f  31 84 f8 00 00 01 07 52  |n..G..J/1......R|
00000160  ef 30 a1 75 09 ae 06 00  1a 14 50 59 a0 72 61 33  |.0.u......PY.ra3|
00000170  d1 55 42 7e 86 83 00 56  00 3f 91 10 89 a9 c5 23  |.UB~...V.?.....#|
00000180  97 d8 66 27 b6 48 71 82  a8 88 08 03 18 05 43 49  |..f'.Hq.......CI|
00000190  a9 03 04 20 ce 5f 08 40  b1 27 f1 49 c7 01 a8 98  |... ._.@.'.I....|
000001a0  94 6c 87 71 83 ff f0 0c  00 34 26 93 40 42 18 51  |.l.q.....4&.@B.Q|
000001b0  7f 20 6a 5c 0b 20 7f fd  80 e2 f8 98 07 60 00 01  |. j\. .......`..|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 4b 8f df 06 00 00  |......?...K.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

It looks like GRUB is installed on sda1, where Windows is installed.  If this is the problem, how do I correct it?

Hey man.  I'm sorry I can't be the one to help you but don't worry.  It is late there may be mroe ppl to help tomorrow.  Was there anything at all weird that hapenned when installing (ive messed my computer up a few times.  Ubuntu isn't very unstable but mistakes can happen.  Also I'm not saying YOU necessarily made a mistake just saying I have and if you did or something weird happens you can add that.  I know how to fix some problems but not right away I could use mroe info if you've got any)

---

### Post by oleink on 2010-05-29
[http://ubuntuforums.org/showthread.php?t=1490763]("http://ubuntuforums.org/showthread.php?t=1490763")

Take a look here that link is ther but also further info!

---

### Post by el_manaba on 2010-05-29
Testdisk did the trick.  Thank you!

---

### Post by bengoerz on 2010-08-27
When I installed Ubuntu 10.04 from USB stick onto a SCSI drive, the installer would incorrectly overwrite the MBR of the USB drive instead of the hard disk. This would result in a blank screen booting from the hard drive, and a "grub geom" error when booting from USB.

I took the easy way out and just installed from CD, which worked.

---

### Post by kenn213 on 2011-02-03
> **bengoerz said:**
> When I installed Ubuntu 10.04 from USB stick onto a SCSI drive, the installer would incorrectly overwrite the MBR of the USB drive instead of the hard disk. This would result in a blank screen booting from the hard drive, and a "grub geom" error when booting from USB.

I took the easy way out and just installed from CD, which worked.

Thank you so much for this. I'm 99% sure thats what my issue is as well. I make a USB stick, the installer boots and works fine, then when I go to reboot into the new system I get a Grub Error booting from the stick, and nothing from the HD. Guess its time to go buy some CD-R's.

---

