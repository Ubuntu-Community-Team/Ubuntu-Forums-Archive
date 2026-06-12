---
title: "Help - Ubuntu 11.04 installation bricked my Win7 drive"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by djpeanut on 2011-05-01
I'm here because everything I've tried has failed...

I was running dual-boot winXP/7 on my desktop PC until a few hours ago. I run Ubuntu on my netbook. I usually use Win7 on the desktop and don't use XP any more, and thought I would replace XP with Ubuntu 11.04. Just for fun.

XP was on an 80GB IDE HD (BIOS calls it primary master), Windows 7 on a 320GB SATA drive (BIOS's tertiary master, secondary master/slave being IDE optical drives).

Windows 7's bootloader used to offer me XP or 7 on startup.

I ran the Ubuntu installation, repartitioned the 80GB drive for Linux and installed. That went fine. The 320GB drive with Windows 7 was untouched by the installer. Or should have been.

Booting into Ubuntu, I first had some graphics issues after logging in. The desktop environment didn't show up, just the desktop background and mouse pointer. The icon for the USB stick I'd used for the installation flickered on and off on the desktop. I Ctrl-Alt-Del'd and the shutdown/restart menu flickered on and off, I managed to click 'Restart' during one flicker. Tried again, booting into Ubuntu Classic, which works fine. No idea why the new interface is broken. Anyway.

Grub doesn't show at startup, and holding Shift brings up the menu containing only Ubuntu x2 and memtest x2. No Windows 7 option in the list. Windows isn't bootable any more.

I unplugged the Ubuntu HD leaving my 320GB Win7 disk plugged in, got Super Grub Disk on my USB stick and tried to boot the Win7 partition on the remaining disk. No message, no nothing, just back to the Super Grub root menu.

The Win 7 disk with the drive labels and partitions and contents show up in Ubuntu's File Manager when I mount them. So the files seem to be there.

I just want to be able to dual boot Win7 or Ubuntu, but can't find any way of booting my Win7 partition any more. The Ubuntu installer, I'm sure, wasn't meant to brick my Win7 drive like this.

Any help would be appreciated. Here's fdisk -l:

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04570456

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2            2551        9730    57667585    5  Extended
/dev/sda5            2551        3037     3906560   82  Linux swap / Solaris
/dev/sda6            3037        9730    53760000   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x59f11ca9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10443    83883366    7  HPFS/NTFS
/dev/sdb2           10444       38913   228685275    7  HPFS/NTFS

Disk /dev/sdc: 8119 MB, 8119648256 bytes
255 heads, 63 sectors/track, 987 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4bd20874

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         987     7928046    b  W95 FAT32


Here's Boot Info Script results.txt:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2dc4.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /ubninit looks at sector 700 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687  83 Linux
/dev/sda2          40,966,142   156,301,311   115,335,170   5 Extended
/dev/sda5          40,966,144    48,779,263     7,813,120  82 Linux swap / Solaris
/dev/sda6          48,781,312   156,301,311   107,520,000  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   167,766,794   167,766,732   7 HPFS/NTFS
/dev/sdb2         167,766,795   625,137,344   457,370,550   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8119 MB, 8119648256 bytes
255 heads, 63 sectors/track, 987 cylinders, total 15858688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    15,856,154    15,856,092   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ec51c77c-1f75-41c4-8712-d8e8edc41424   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e7509702-b49a-4039-b83f-a454d34d9188   swap                                     
/dev/sda6        89d7de8a-738a-43c5-acd5-34f11da9d8ad   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BA505D5F505D2403                       ntfs       Windows 7                     
/dev/sdb2        FC34B62C34B5EA32                       ntfs       Storage 2                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        10F9-5D3C                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/Storage 2         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ec51c77c-1f75-41c4-8712-d8e8edc41424
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ec51c77c-1f75-41c4-8712-d8e8edc41424
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ec51c77c-1f75-41c4-8712-d8e8edc41424
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ec51c77c-1f75-41c4-8712-d8e8edc41424 ro  vga=795  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ec51c77c-1f75-41c4-8712-d8e8edc41424
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ec51c77c-1f75-41c4-8712-d8e8edc41424 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ec51c77c-1f75-41c4-8712-d8e8edc41424
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ec51c77c-1f75-41c4-8712-d8e8edc41424
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=89d7de8a-738a-43c5-acd5-34f11da9d8ad /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  10.9GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.38-8-generic
  17.3GB: boot/vmlinuz-2.6.38-8-generic
   1.7GB: initrd.img
  17.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  9a e2 c1 58 d6 ed 64 0b  2b 2f 28 af a2 11 48 83  |...X..d.+/(...H.|
00000010  63 c5 96 9c 91 ff 00 e1  70 8c 75 d5 90 d3 50 a0  |c.......p.u...P.|
00000020  7f 9b fe c1 52 6f 3d 34  88 d4 d3 62 49 44 72 43  |....Ro=4...bIDrC|
00000030  6c e2 59 08 8e 39 62 86  26 1c 4f db 3f e8 e8 43  |l.Y..9b.&.O.?..C|
00000040  31 fd a6 c7 c2 f3 40 d2  f9 fe 37 ff 00 8a 5f 1f  |1.....@...7..._.|
00000050  9d 2d 56 3b 87 86 c5 6d  24 57 8a 68 22 57 69 3d  |.-V;...m$W.h"Wi=|
00000060  59 05 fa 5e 3f aa e4 03  c7 e1 a2 7f 93 83 c3 f3  |Y..^?...........|
00000070  fc 70 f0 a0 e9 ce db df  fd 21 c0 c5 a7 94 cd 3c  |.p.......!.....<|
00000080  b3 11 43 2b b3 90 3b 16  24 d3 f1 cb 43 94 05 0a  |..C+..;.$...C...|
00000090  58 01 3d 05 7b ed 85 2e  c5 5d 8a b2 48 7e 0f cb  |X.=.{....]..H~..|
000000a0  ab a3 fe fd d5 62 1f f0  10 13 fc 73 9c c9 bf 6c  |.....b.....s...l|
000000b0  43 fa 1a 59 ff 00 b2 ca  c7 f8 98 de 74 6c 9d 8a  |C..Y........tl..|
000000c0  b5 fd 70 2b ff d0 ea 6f  f6 cf cc fe bc f0 89 f3  |..p+...o........|
000000d0  2f 5e 39 2d c8 a5 b5 fb  43 e7 80 ab 19 f2 07 c3  |/^9-....C.......|
000000e0  a3 5d c5 fe f9 d4 6f 13  fe 4a d7 f8 e7 4d ed 4e  |.]....o..J...M.N|
000000f0  fa 88 4b f9 fa 7c 12 ff  00 a5 6c a5 cd 92 e7 34  |..K..|....l....4|
00000100  c5 d8 ab b1 57 62 ae c5  5d 8a bb 15 76 2a ec 55  |....Wb..]...v*.U|
00000110  d8 ab b1 57 62 ae c5 5d  8a a2 6d 2d f9 9e 6c 3e  |...Wb..]..m-..l>|
00000120  11 d0 78 9c ce d1 e9 b8  8f 11 fa 5a 72 ce b6 08  |..x........Zr...|
00000130  ec dc 38 ce c5 5d 8a a9  4d 73 1c 5b 1d db f9 46  |..8..]..Ms.[...F|
00000140  63 66 d4 c7 1f 99 6c 8e  32 50 8f 77 33 74 3c 47  |cf....l.2P.w3t<G|
00000150  80 cd 6e 4d 64 e5 cb d2  df 1c 40 28 92 c7 a9 27  |..nMd.....@(...'|
00000160  31 4c 89 e6 d9 4d 60 56  c1 23 a1 23 08 91 0b 4a  |1L...M`V.#.#...J|
00000170  b1 dd cc 9d f9 0f 03 99  38 f5 93 8f 5e 26 b3 88  |........8...^&..|
00000180  14 5c 37 51 c9 b7 d9 6f  03 fc 33 65 87 57 19 ed  |.\7Q...o..3e.W..|
00000190  f4 c9 a2 58 c8 56 cc a6  b7 62 ae c0 ac 6b cd 30  |...X.V...b...k.0|
000001a0  e8 3a 3e 97 3e ac 3c 9f  a7 eb 72 23 99 6f 19 d5  |.:>.>.<...r#.o..|
000001b0  63 94 21 dd a4 af 07 e7  c7 f6 b3 ac ec 5e 00 fe  |c.!..........^..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 38 77 00 00 fe  |...........8w...|
000001d0  ff ff 05 fe ff ff 02 38  77 00 00 a8 68 06 00 00  |.......8w...h...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 22 00  |.X.SYSLINUX...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  dc f1 f1 00 5f 3c 00 00  00 00 00 00 02 00 00 00  |...._<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 3c 5d f9 10 4e  4f 20 4e 41 4d 45 20 20  |..)<]..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 60  84 00 00 66 ba 00 00 00  |..E}.f.`...f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

The 3rd disk is my USB stick...

Please help!

---

### Post by kansasnoob on 2011-05-01
**[COLOR="Red"]Read this all before beginning[/COLOR]** and if you have any questions ask before beginning!

Looking at your BIS output I see no "/bootmgr /Boot/BCD" files for Win 7 :(

I'd assume that since Win XP existed when Win 7 was installed that Win 7 made use of the existing XP boot files.

Anyway, I'm 90% sure we can fix that. You'll first need to DL and burn this disc:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

(I assume you'll know if you need 32 or 64 bit.)

**Note**: If you have the Win 7 install disc you can use that, just be very, very careful that you don't start a full recovery!

Once you have that disc burned insert it, reboot and enter the BIOS, again I'm assuming you know how, and set the hard disc boot priority so the 320GB drive will boot first. After saving that to the BIOS your system should boot the new CD.

At the first screen select your favorite language.
At the second screen choose "Repair your Computer".

If a pop up appears, offering to repair a problem with the "Startup options", click on "Repair and restart".

Otherwise, on the next screen select "Use recovery tools ..." and click on "Next".
Choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you'll have to run "Startup Repair" at least twice, a third or even fourth time will not hurt.

When done enter the BIOS again, change the hard disc boot priority back to the 80GB drive and once you've booted into Ubuntu (using either the classic or classic w/o effects DE) open the terminal and run this command:

```
sudo update-grub
```

Hopefully that will find Win 7 :)

---

### Post by djpeanut on 2011-05-01
Thank you for your reply. I have no CDRs to hand - is it possible to use a USB stick to run the Win7 recovery process?

If not, I will go and get a CDR tomorrow and let you know how I get on.

:popcorn:

---

### Post by kansasnoob on 2011-05-02
I've never tried it on USB so I really don't know, but I see no instructions at the Neosmart site for USB.

Reading over what I typed yesterday I do however see I left one thing out, looking at the output of fdisk:

```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687  83 Linux
/dev/sda2          40,966,142   156,301,311   115,335,170   5 Extended
/dev/sda5          40,966,144    48,779,263     7,813,120  82 Linux swap / Solaris
/dev/sda6          48,781,312   156,301,311   107,520,000  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   167,766,794   167,766,732   7 HPFS/NTFS
/dev/sdb2         167,766,795   625,137,344   457,370,550   7 HPFS/NTFS

```

I see there is no boot flag set on sdb1, the Win 7 partition. That also needs to be fixed and the easiest way is to use Gparted which is available on the Live CD or you can install it in your new Ubuntu by running:

```
sudo apt-get install gparted
```

You'll then find it in System > Administration, example:

[ATTACH]190806[/ATTACH]

I think that's fairly self explanatory :D

You need a boot flag set on the Win 7 partition, sdb1 ATM.

Sorry I forgot to mention that yesterday.

---

### Post by djpeanut on 2011-05-02
Huge thanks. I got it sorted with your instructions. The Win7 recovery on USB didn't work out, but I burned a CD in the end. It took a while to notice the boot flag was missing, but I fixed that eventually with the diskpart util on the Win7 disk. All back to normal - thank goodness :)

---

### Post by kansasnoob on 2011-05-02
Glad things worked out for you :)

Could I get you to use the thread tools to mark this solved?

---

