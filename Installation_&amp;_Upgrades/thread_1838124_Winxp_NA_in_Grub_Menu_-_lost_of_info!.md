---
title: "Winxp NA in Grub Menu - lost of info!"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by sandman3838 on 2011-09-03
Good day!



I hoping that someone could help with this one.

WinXP isn't showing up in my grub menu after I ran "Sudo Update-Grub"



I just did a clean install of everything.

Winxp / Win_7 / Ubuntu 10.10



I installed each drive separately and by themselves.  



500GB HD Winxp/Games

250GB HD Win_7

200GB HD Ubuntu 10.10



My last step after installing Ubuntu and letting it do all of the OS's upgrades was to re-connect the drives.  i then went into the BIOS and placed the drives in this boot order.



1 - 200GB HD Ubuntu 10.10

2 - 250GB HD Win_7

3 - 500GB HD Winxp/Games



I booted up into Ubuntu and in terminal I ran "Sudo Update-Grub" the results were:


```

Generating grub.cfg ...

Found linux image: /boot/vmlinuz-2.6.35-30-generic

Found initrd image: /boot/initrd.img-2.6.35-30-generic

Found linux image: /boot/vmlinuz-2.6.35-22-generic

Found initrd image: /boot/initrd.img-2.6.35-22-generic

Found memtest86+ image: /boot/memtest86+.bin

Found Windows 7 (loader) on /dev/sda1

Found Windows 7 (loader) on /dev/sdc1

done

```


Ubuntu is ok as is the first Win_7 however the second Win_7 does nothing and there is no mention of Win_XP?



I don't mind leaving the Second Dead listing of Win_7 I can live with that.  One head ache at a time.  I would just like to get Winxp in there.  Below I have added in some more information that might help?





*** post the output of sudo fdisk -l **** 
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0x66305c95



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1          13      102400    7  HPFS/NTFS

Partition 1 does not end on cylinder boundary.

/dev/sda2              13       30402   244092928    7  HPFS/NTFS

Partition 2 does not end on cylinder boundary.



Disk /dev/sdb: 200.0 GB, 200049647616 bytes

255 heads, 63 sectors/track, 24321 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0x000b7609



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       23330   187395072   83  Linux

/dev/sdb2           23330       24322     7963649    5  Extended

/dev/sdb5           23330       24322     7963648   82  Linux swap / Solaris



Disk /dev/sdc: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0xc7a3ff02



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *           1       25560   205310668+   7  HPFS/NTFS

/dev/sdc2           25561       60801   283073332    f  W95 Ext'd (LBA)

/dev/sdc5           25561       60801   283073300+   7  HPFS/NTFS

```

```

=================   SCRIPT HD INFO   ===============  




                  Boot Info Script 0.60    from 17 May 2011




============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdc5 and looks at sector 272191 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdc5 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   488,392,703   488,185,856   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   374,792,191   374,790,144  83 Linux
/dev/sdb2         374,794,238   390,721,535    15,927,298   5 Extended
/dev/sdb5         374,794,240   390,721,535    15,927,296  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   410,621,399   410,621,337   7 NTFS / exFAT / HPFS
/dev/sdc2         410,621,401   976,768,064   566,146,664   f W95 Extended (LBA)
/dev/sdc5         410,621,464   976,768,064   566,146,601   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FCBC8E93BC8E485A                       ntfs       System Reserved
/dev/sda2        96B094ECB094D459                       ntfs       WIN_7
/dev/sdb1        ac5c5809-0d98-4b33-bbb6-eaaf06d07f79   ext4       
/dev/sdb5        7bd0fff9-8368-4171-94ca-4ca93bde98d1   swap       
/dev/sdc1        01CC639612EEB5E0                       ntfs       Win_XP
/dev/sdc5        01CC63B9472C58D0                       ntfs       GAMES

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set ac5c5809-0d98-4b33-bbb6-eaaf06d07f79
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set ac5c5809-0d98-4b33-bbb6-eaaf06d07f79
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ac5c5809-0d98-4b33-bbb6-eaaf06d07f79
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=ac5c5809-0d98-4b33-bbb6-eaaf06d07f79 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ac5c5809-0d98-4b33-bbb6-eaaf06d07f79
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=ac5c5809-0d98-4b33-bbb6-eaaf06d07f79 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ac5c5809-0d98-4b33-bbb6-eaaf06d07f79
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ac5c5809-0d98-4b33-bbb6-eaaf06d07f79 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ac5c5809-0d98-4b33-bbb6-eaaf06d07f79
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ac5c5809-0d98-4b33-bbb6-eaaf06d07f79 ro single 
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
	search --no-floppy --fs-uuid --set ac5c5809-0d98-4b33-bbb6-eaaf06d07f79
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ac5c5809-0d98-4b33-bbb6-eaaf06d07f79
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set FCBC8E93BC8E485A
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01CC639612EEB5E0
	chainloader +1
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ac5c5809-0d98-4b33-bbb6-eaaf06d07f79 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7bd0fff9-8368-4171-94ca-4ca93bde98d1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.134788513 = 21.619564544   boot/grub/core.img                             1
 108.221847534 = 116.202323968  boot/grub/grub.cfg                             1
   1.063476562 = 1.141899264    boot/initrd.img-2.6.35-22-generic              2
   1.086914062 = 1.167065088    boot/initrd.img-2.6.35-30-generic              2
  20.255016327 = 21.748658176   boot/vmlinuz-2.6.35-22-generic                 1
  20.261249542 = 21.755351040   boot/vmlinuz-2.6.35-30-generic                 1
   1.086914062 = 1.167065088    initrd.img                                     2
   1.063476562 = 1.141899264    initrd.img.old                                 2
  20.261249542 = 21.755351040   vmlinuz                                        1
  20.255016327 = 21.748658176   vmlinuz.old                                    1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  c4 06 de 3d 12 80 30 7b  e6 3f 7d ed 68 21 84 24  |...=..0{.?}.h!.$|
00000010  f5 5e 21 10 7d fc 2d c9  e4 40 61 98 b7 57 e2 33  |.^!.}.-..@a..W.3|
00000020  d3 01 b0 98 23 7b 13 89  4d a4 b6 da a1 4a 4f 82  |....#{..M....JO.|
00000030  d5 25 4d 16 60 7b c5 b1  a4 73 ab e0 8b 45 66 41  |.%M.`{...s...EfA|
00000040  8b 82 1f 92 f9 34 b8 a2  b6 c6 28 c0 60 20 ac 0a  |.....4....(.` ..|
00000050  aa d0 de 05 62 c0 86 ab  f3 47 3e 1b 23 e2 05 04  |....b....G>.#...|
00000060  f0 f4 0d 98 4d fe 4e 4e  59 16 37 c7 92 97 d0 6e  |....M.NNY.7....n|
00000070  88 44 b0 94 07 10 0d 07  49 6a f7 3b 25 de fe 54  |.D......Ij.;%..T|
00000080  67 84 7e ed 86 cd 48 77  a1 b0 55 03 32 01 85 c0  |g.~...Hw..U.2...|
00000090  a3 10 b4 b9 3b 11 45 b2  de 70 73 9b 04 5c d2 57  |....;.E..ps..\.W|
000000a0  03 51 b0 0e 06 1d 81 e6  13 a6 f2 76 52 a4 54 3f  |.Q.........vR.T?|
000000b0  d6 28 8c de cd 55 5a 6b  80 a6 d1 c7 c6 f2 f5 7e  |.(...UZk.......~|
000000c0  1e 16 c5 d6 b4 6e 8d 09  e0 57 02 8c 03 87 42 5a  |.....n...W....BZ|
000000d0  46 c1 94 fa 8e 26 0e 5b  fa ad be 64 3c e7 3f 2e  |F....&.[...d<.?.|
000000e0  21 ce 09 d5 c0 d8 88 4a  06 1f 96 d4 83 e1 0c 19  |!......J........|
000000f0  37 c0 39 25 91 80 55 b5  37 ca 95 42 ce 35 d5 33  |7.9%..U.7..B.5.3|
00000100  22 81 38 4a 08 0d ab f2  a9 89 2d df 7e 95 7b a8  |".8J......-.~.{.|
00000110  bb 56 e5 25 8b 8a 03 a7  81 14 4b 05 10 21 8e b0  |.V.%......K..!..|
00000120  20 a4 06 56 c2 58 c4 00  e5 5f 4f 30 7b ef e5 2a  | ..V.X..._O0{..*|
00000130  52 8b 54 e0 10 43 44 57  0c c1 b3 c0 1a 3e 03 c2  |R.T..CDW.....>..|
00000140  34 2f c1 c0 96 9b d3 cd  e5 bd 52 20 52 cf 6f 78  |4/........R R.ox|
00000150  84 2e 61 6a fb 6b c3 62  95 45 e2 4c ab fa ce 23  |..aj.k.b.E.L...#|
00000160  52 46 48 41 4e d8 df d9  05 05 87 82 58 29 fd 9a  |RFHAN.......X)..|
00000170  9d a5 1f e0 c4 4c 2f f6  7b f3 b9 04 ce a1 b3 9e  |.....L/.{.......|
00000180  ba 1c bc b7 a9 39 88 c8  6d 60 99 5c f9 f9 03 f7  |.....9..m`.\....|
00000190  43 d7 44 72 f0 04 ed 22  b8 69 6e 21 99 0b 66 19  |C.Dr...".in!..f.|
000001a0  df 33 dd b1 fe 1b e6 55  57 97 b6 e0 cd d1 ae 4b  |.3.....UW......K|
000001b0  f9 c8 67 c0 fa b6 5b 97  ae 1b 8f c4 74 c0 00 fe  |..g...[.....t...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 f3 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc2

00000000  05 00 4e 00 54 00 4c 00  44 00 52 00 04 00 24 00  |..N.T.L.D.R...$.|
00000010  49 00 33 00 30 00 00 e0  00 00 00 30 00 00 00 00  |I.3.0......0....|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 eb 12  90 90 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 8c c8 8e d8 c1 e0  |................|
00000070  04 fa 8b e0 fb e8 03 fe  66 0f b7 06 0b 00 66 0f  |........f.....f.|
00000080  b6 1e 0d 00 66 f7 e3 66  a3 4e 02 66 8b 0e 40 00  |....f..f.N.f..@.|
00000090  80 f9 00 0f 8f 0e 00 f6  d9 66 b8 01 00 00 00 66  |.........f.....f|
000000a0  d3 e0 eb 08 90 66 a1 4e  02 66 f7 e1 66 a3 52 02  |.....f.N.f..f.R.|
000000b0  66 0f b7 1e 0b 00 66 33  d2 66 f7 f3 66 a3 56 02  |f.....f3.f..f.V.|
000000c0  e8 0d 04 66 8b 0e 4a 02  66 89 0e 22 02 66 03 0e  |...f..J.f..".f..|
000000d0  52 02 66 89 0e 26 02 66  03 0e 52 02 66 89 0e 2a  |R.f..&.f..R.f..*|
000000e0  02 66 03 0e 52 02 66 89  0e 3a 02 66 03 0e 52 02  |.f..R.f..:.f..R.|
000000f0  66 89 0e 42 02 66 b8 90  00 00 00 66 8b 0e 22 02  |f..B.f.....f..".|
00000100  e8 ec 08 66 0b c0 0f 84  57 fe 66 a3 2e 02 66 b8  |...f....W.f...f.|
00000110  a0 00 00 00 66 8b 0e 26  02 e8 d3 08 66 a3 32 02  |....f..&....f.2.|
00000120  66 b8 b0 00 00 00 66 8b  0e 2a 02 e8 c1 08 66 a3  |f.....f..*....f.|
00000130  36 02 66 a1 2e 02 66 0b  c0 0f 84 24 fe 67 80 78  |6.f...f....$.g.x|
00000140  08 00 0f 85 1b fe 67 66  8d 50 10 67 03 42 04 67  |......gf.P.g.B.g|
00000150  66 0f b6 48 0c 66 89 0e  62 02 67 66 8b 48 08 66  |f..H.f..b.gf.H.f|
00000160  89 0e 5e 02 66 a1 5e 02  66 0f b7 0e 0b 00 66 33  |..^.f.^.f.....f3|
00000170  d2 66 f7 f1 66 a3 66 02  66 a1 42 02 66 03 06 5e  |.f..f.f.f.B.f..^|
00000180  02 66 a3 46 02 66 83 3e  32 02 00 0f 84 19 00 66  |.f.F.f.>2......f|
00000190  83 3e 36 02 00 0f 84 c8  fd 66 8b 1e 36 02 1e 07  |.>6......f..6...|
000001a0  66 8b 3e 46 02 e8 92 01  66 0f b7 0e 00 02 66 b8  |f.>F....f.....f.|
000001b0  02 02 00 00 e8 96 07 66  0b c0 0f 84 0a 09 00 fe  |.......f........|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 29 b6 be 21 00 00  |......?...)..!..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by sandman3838 on 2011-09-03
Good afternoon!

I have been doing some reading!

If I understand it correctly, it looks like it's seeing WinXp on sdc1 but it's giving it a label of WINDOWS 7 on the second entry.  For what ever reason it's just gives me a blinking cursor.

I should mention that if unplug the other OS Hds I go right into Windows XP without a hitch.

Eventually I will just use "Grub Customizer" to uncheck or hide the current WWINDOWS 7 (Sdc1) entry. But back you getting an entry that will work.

I was thinking about adding in my own custom file or add the entry in

/etc/grub.d/40_custom 

or create my own file name and adding in the following:


menuentry "Windows XP (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 01CC639612EEB5E0
    drivemap -s (hd0) ${root}
    chainloader +1
}

However I know the the "Set Root=" and "Drivemap" lines are wrong!

Suggections?

---

### Post by sandman3838 on 2011-09-04
Got it I added this to the 40 file:

menuentry "Microsoft Windows XP Pro (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 01CC639612EEB5E0
drivemap -s (hd0) ${root}
chainloader +1
}


Its now working just fine

---

