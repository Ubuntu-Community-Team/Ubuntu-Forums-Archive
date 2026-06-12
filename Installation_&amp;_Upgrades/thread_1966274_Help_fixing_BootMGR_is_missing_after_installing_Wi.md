---
title: "Help fixing BootMGR is missing after installing Windows 7 and then Ubuntu 12.04."
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by krej on 2012-04-26
Today I decided to reinstall both Windows 7 and Ubuntu, and now I can't boot off of Windows.

I have 3 harddrives. One of them is a SSD where I have Windows installed as well as the root partition of Ubuntu. Then I have another HDD with my /home and swap partitions. The third is just a drive full of data that isn't related.

I started with my HDD has the first device to boot off of(I don't know why it was set like that) but I installed Windows to my SSD. After installing Windows, I could boot into it with no problems. Then I installed Ubuntu and told it to install grub onto my SSD.

After installing Ubuntu, when I booted my computer it said there was no drive to boot off of. So I went into my BIOS and changed the primary boot drive to be my SSD, and now I am able to boot into Ubuntu.

There was no GRUB entry for Windows by default, so I added it following [this guide]("http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/"). Now when I try to boot into it, I get the BootMGR is missing error.

I've tried running the startup repair on the Windows install DVD, and it said it fixed something, but the error didn't change. I've tried running bootrec.exe /fixboot off of the Windows DVD, and it said it completed successfully, but the error is still there.

Can anyone help me get booting into Windows? Here is my bootinfoscript log:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   488,488,959   488,486,912  83 Linux
/dev/sda2         488,491,006   496,394,239     7,903,234   5 Extended
/dev/sda5         488,491,008   496,394,239     7,903,232  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 90.0 GB, 90028302336 bytes
255 heads, 63 sectors/track, 10945 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   134,875,135   134,873,088   7 NTFS / exFAT / HPFS
/dev/sdc2         134,877,182   175,835,135    40,957,954   5 Extended
/dev/sdc5         134,877,184   175,835,135    40,957,952  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        90f86081-f9e6-4d11-85b0-ac318b019c79   ext4       
/dev/sda5        a2a37667-cbf2-4019-b08a-1646033efc90   swap       
/dev/sdb1        EA4A791F4A78E9A9                       ntfs       Games
/dev/sdc1        32BC8A22BC89E129                       ntfs       
/dev/sdc5        bb7a6c3e-b343-4511-9a8a-5502dc148b3d   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /home                    ext4       (rw)
/dev/sdc5        /                        ext4       (rw,errors=remount-ro)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root bb7a6c3e-b343-4511-9a8a-5502dc148b3d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos5)'
  search --no-floppy --fs-uuid --set=root bb7a6c3e-b343-4511-9a8a-5502dc148b3d
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7a6c3e-b343-4511-9a8a-5502dc148b3d
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=bb7a6c3e-b343-4511-9a8a-5502dc148b3d ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7a6c3e-b343-4511-9a8a-5502dc148b3d
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=bb7a6c3e-b343-4511-9a8a-5502dc148b3d ro recovery nomodeset 
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
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7a6c3e-b343-4511-9a8a-5502dc148b3d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7a6c3e-b343-4511-9a8a-5502dc148b3d
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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=bb7a6c3e-b343-4511-9a8a-5502dc148b3d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=90f86081-f9e6-4d11-85b0-ac318b019c79 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a2a37667-cbf2-4019-b08a-1646033efc90 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  b6 c2 a1 c7 13 5d ed 82  ae ec cc dd 82 67 84 12  |.....].......g..|
00000010  e7 f5 cd 76 bc a2 14 e9  95 e9 8e 60 03 50 ea 56  |...v.......`.P.V|
00000020  b5 87 c0 c1 ac 27 89 a8  fb 7c 2c 59 a9 43 ae 68  |.....'...|,Y.C.h|
00000030  cb a4 09 d5 f6 b8 77 a3  85 0f de e4 84 d3 07 17  |......w.........|
00000040  ec a4 d0 8d 85 d8 f3 19  96 96 05 d4 a1 c6 67 74  |..............gt|
00000050  a9 4c f1 af 8a 79 45 25  e1 3c 30 e9 13 b3 9a e3  |.L...yE%.<0.....|
00000060  6d 2b df 8b cd 5d 77 c2  8c 0b 57 f5 b6 a7 92 1f  |m+...]w...W.....|
00000070  5b 55 e6 b4 1e d5 df dd  c3 72 ad 75 0e 15 3a 70  |[U.......r.u..:p|
00000080  52 3a 42 91 c8 a8 46 35  12 02 89 92 91 a9 81 62  |R:B...F5.......b|
00000090  37 2b f7 05 f4 f5 6d 4a  2b 83 94 52 e3 2f a8 c5  |7+....mJ+..R./..|
000000a0  52 e3 67 7d 07 0e 58 dd  77 66 57 c5 cc 4f 80 ef  |R.g}..X.wfW..O..|
000000b0  e4 0e 9a f1 33 64 81 6e  b6 63 a5 57 b6 9e a9 a9  |....3d.n.c.W....|
000000c0  a9 77 62 96 f5 cf b4 78  13 c9 5d fe 63 13 63 d9  |.wb....x..].c.c.|
000000d0  95 45 44 fd c7 1d 48 5b  4c 64 b6 2d 1d e4 dd ab  |.ED...H[Ld.-....|
000000e0  15 91 aa ca c7 f7 ef 9e  b6 19 98 5e e9 09 8b b9  |...........^....|
000000f0  c2 63 5c c6 00 1f 11 13  4e 99 66 6c 32 11 5b 1a  |.c\.....N.fl2.[.|
00000100  61 b5 8f 32 31 7d 2c 42  7d ae 2c cc 37 78 63 f4  |a..21},B}.,.7xc.|
00000110  e1 be 0d 0c ae 89 bf bd  98 ba 52 e0 64 d8 58 dd  |..........R.d.X.|
00000120  5c 1a ba b0 10 e8 6d 90  3b e1 f2 01 0a bd 13 f9  |\.....m.;.......|
00000130  9c a9 d4 27 e8 86 ea 90  5d f4 87 af a2 62 23 f0  |...'....]....b#.|
00000140  c9 39 e4 79 15 17 6f a9  cf bb 30 35 c2 f2 99 fb  |.9.y..o...05....|
00000150  c7 c6 d6 cf 61 5d 58 60  ec ca 66 3c 28 03 d1 87  |....a]X`..f<(...|
00000160  70 a1 de 36 43 27 b4 e4  61 59 e6 44 e3 f8 f5 28  |p..6C'..aY.D...(|
00000170  3e 57 f5 d1 77 af ee 75  8e a6 6c 76 b5 6d 3c b7  |>W..w..u..lv.m<.|
00000180  a7 4b 3b 2f b5 df 68 20  df 0a b2 76 73 d4 ec cf  |.K;/..h ...vs...|
00000190  27 8f 76 f8 dc 70 60 1a  72 70 c5 96 bf 28 a5 e5  |'.v..p`.rp...(..|
000001a0  7a d3 4c 70 ed 0d f0 a1  5b f4 30 67 77 e0 8d be  |z.Lp....[.0gw...|
000001b0  46 dd 62 87 e8 1e 4f 10  7d 4d 84 04 23 70 00 fe  |F.b...O.}M..#p..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 78 00 00 00  |............x...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc2

00000000  00 00 00 2f 11 00 00 03  00 04 00 00 00 2f 11 00  |.../........./..|
00000010  00 03 00 08 00 00 00 2e  11 00 00 03 00 01 0e 01  |................|
00000020  00 0e 42 00 00 48 89 4c  24 08 48 8b 44 24 08 48  |..B..H.L$.H.D$.H|
00000030  8b 00 c3 04 00 00 00 f1  00 00 00 9d 00 00 00 66  |...............f|
00000040  00 10 11 00 00 00 00 00  00 00 00 00 00 00 00 0e  |................|
00000050  00 00 00 05 00 00 00 0d  00 00 00 10 18 00 00 00  |................|
00000060  00 00 00 00 00 00 41 54  4c 3a 3a 43 53 69 6d 70  |......ATL::CSimp|
00000070  6c 65 53 74 72 69 6e 67  54 3c 77 63 68 61 72 5f  |leStringT<wchar_|
00000080  74 2c 30 3e 3a 3a 6f 70  65 72 61 74 6f 72 20 77  |t,0>::operator w|
00000090  63 68 61 72 5f 74 20 63  6f 6e 73 74 20 2a 20 5f  |char_t const * _|
000000a0  5f 70 74 72 36 34 00 1c  00 12 10 00 00 00 00 00  |_ptr64..........|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 20 40 01 00 11 00 11  11 08 00 00 00 0e 18 00  |. @.............|
000000d0  00 4f 01 74 68 69 73 00  02 00 06 00 00 00 00 f2  |.O.this.........|
000000e0  00 00 00 30 00 00 00 00  00 00 00 00 00 00 00 0e  |...0............|
000000f0  00 00 00 78 00 00 00 03  00 00 00 24 00 00 00 00  |...x.......$....|
00000100  00 00 00 92 01 00 80 05  00 00 00 93 01 00 80 0d  |................|
00000110  00 00 00 94 01 00 80 2c  00 00 00 34 11 00 00 0b  |.......,...4....|
00000120  00 30 00 00 00 34 11 00  00 0a 00 b4 00 00 00 34  |.0...4.........4|
00000130  11 00 00 0b 00 b8 00 00  00 34 11 00 00 0a 00 48  |.........4.....H|
00000140  89 4c 24 08 48 83 ec 28  48 8b 4c 24 30 e8 00 00  |.L$.H..(H.L$0...|
00000150  00 00 8b 40 08 48 83 c4  28 c3 0f 00 00 00 6e 12  |...@.H..(.....n.|
00000160  00 00 04 00 04 00 00 00  f1 00 00 00 86 00 00 00  |................|
00000170  4f 00 10 11 00 00 00 00  00 00 00 00 00 00 00 00  |O...............|
00000180  1b 00 00 00 09 00 00 00  16 00 00 00 16 18 00 00  |................|
00000190  00 00 00 00 00 00 00 41  54 4c 3a 3a 43 53 69 6d  |.......ATL::CSim|
000001a0  70 6c 65 53 74 72 69 6e  67 54 3c 77 63 68 61 72  |pleStringT<wchar|
000001b0  5f 74 2c 30 3e 3a 3a 47  65 74 4c 65 6e 67 00 fe  |_t,0>::GetLeng..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f8 70 02 00 00  |............p...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
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

```

---

### Post by krej on 2012-04-26
Nevermind guys, I found the answer! Before running the start up repair on the Windows DVD, running os-probe found nothing, so I didn't think that worked at all. However, after I ran the startup repair, it said it fixed something(even though I still couldn't boot it), and then I ran os-probe again and Ubuntu found Windows 7 and added it to grub for me, and now it boots!

---

### Post by oldfred on 2012-04-26
When you installed Windows to sdc, it installed a 100MB boot/repair partition to sda and the main ( or c: partition to sdc). 

Then it looks like you formated sda to a Linux partition and overwrote that boot partition. Your Windows repairs then reinstalled the boot files that were in the boot partition to your main partition in sdc. 

Then you sudo update-grub found Windows in sdc as it had all the boot files.

With multiple drives & multiple systems you have to set boot drive first in BIOS and pay attention to where boot loaders or boot partitions get installed. 

I run boot script both before & after every major system change just to be sure of where everything is at and if it went where I thought it did.

---

