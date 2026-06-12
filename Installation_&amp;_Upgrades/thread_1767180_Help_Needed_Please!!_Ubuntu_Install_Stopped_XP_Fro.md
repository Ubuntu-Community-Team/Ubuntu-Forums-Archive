---
title: "Help Needed Please!! Ubuntu Install Stopped XP From Booting"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by neomaxin on 2011-05-25
I had Windows XP SP2 on my first hard drive, I then resized and installed Ubuntu v11 now when my PC boot us I can see the Grub 2 boot screen I can see windows an Ubuntu, Ubuntu boots fine but I'm left with a blank screen with a white blinking cursor every time I try to boot into Windows XP

here is a copy of my Boot Info Script



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

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
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   134,144,306   134,144,244   7 NTFS / exFAT / HPFS
/dev/sda2         134,146,046   156,301,311    22,155,266   5 Extended
/dev/sda5         155,387,904   156,301,311       913,408  82 Linux swap / Solaris
/dev/sda6         134,146,048   154,472,447    20,326,400  83 Linux
/dev/sda7         154,474,496   155,379,711       905,216  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   160,055,594   160,055,532   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6ABCE7D0BCE7953B                       ntfs       Windows
/dev/sda5        1627e01c-390d-4383-8fca-21277989e490   swap       
/dev/sda6        652a8fcb-c177-402d-98b9-4194a84e0884   ext4       
/dev/sda7        4b6366bf-56c7-48a5-9a72-3e5a83a6e1a1   swap       
/dev/sdb1        8CF86607F865EFBE                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect  
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.1="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /safeboot:minimal 
--------------------------------------------------------------------------------

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 652a8fcb-c177-402d-98b9-4194a84e0884
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 652a8fcb-c177-402d-98b9-4194a84e0884
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 652a8fcb-c177-402d-98b9-4194a84e0884
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=652a8fcb-c177-402d-98b9-4194a84e0884 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 652a8fcb-c177-402d-98b9-4194a84e0884
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=652a8fcb-c177-402d-98b9-4194a84e0884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 652a8fcb-c177-402d-98b9-4194a84e0884
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 652a8fcb-c177-402d-98b9-4194a84e0884
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6ABCE7D0BCE7953B
    drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4b6366bf-56c7-48a5-9a72-3e5a83a6e1a1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  65.002887726 = 69.796319232   boot/grub/core.img                             1
  66.587142944 = 71.497400320   boot/grub/grub.cfg                             1
  65.528194427 = 70.360363008   boot/initrd.img-2.6.38-8-generic               3
  65.135108948 = 69.938290688   boot/vmlinuz-2.6.38-8-generic                  2
  65.528194427 = 70.360363008   initrd.img                                     3
  65.135108948 = 69.938290688   vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  16 90 29 4f 2c 17 30 c8  44 d2 00 62 51 73 ef b3  |..)O,.0.D..bQs..|
00000010  ce 81 9b 8b 4a a0 b6 74  66 58 c6 0e e9 b4 f1 dd  |....J..tfX......|
00000020  4c 88 59 3b 1a 80 b8 ba  1e 3d 08 c9 3c 47 a6 d3  |L.Y;.....=..<G..|
00000030  91 52 12 54 f8 cb 38 94  06 f8 78 24 6d e1 60 e3  |.R.T..8...x$m.`.|
00000040  83 4e 11 21 fb 9d 09 bd  ce af 42 f7 3e ae 35 1a  |.N.!......B.>.5.|
00000050  02 4e ba d2 53 40 b2 57  b8 f9 43 21 42 83 1c 70  |.N..S@.W..C!B..p|
00000060  5a e1 e7 39 26 5c 3c 82  79 89 c3 3a 78 14 7a eb  |Z..9&\<.y..:x.z.|
00000070  24 4e f3 8c 11 0d 1b cd  be b7 ca 9d 05 38 3f 38  |$N...........8?8|
00000080  b6 80 64 2b c6 8e 7a 76  90 d5 ce 6d cf 3a be 0a  |..d+..zv...m.:..|
00000090  d7 f6 e7 27 80 e1 d9 16  1a 69 69 11 1d 45 d8 6d  |...'.....ii..E.m|
000000a0  95 e2 5d 83 17 a7 f7 1b  2d e1 c1 1c 82 e2 90 76  |..].....-......v|
000000b0  8c 44 e9 fd a9 49 fb a5  12 0a ba b6 5c 23 b0 13  |.D...I......\#..|
000000c0  53 da 05 30 bc d7 52 22  ea 48 74 8d f7 df 7d ac  |S..0..R".Ht...}.|
000000d0  ea 3c 2a 1a 0c 85 ab df  77 2a fe c0 61 37 eb af  |.<*.....w*..a7..|
000000e0  7d ac 8c 97 5f 3c f2 77  5f 1a 68 15 82 f4 de 0c  |}..._<.w_.h.....|
000000f0  4f 53 43 93 a4 ab bb cb  4f 11 8c d4 6a 4c e3 8e  |OSC.....O...jL..|
00000100  23 d5 d5 a0 30 33 81 d8  cc e7 8d 88 58 ed ce e3  |#...03......X...|
00000110  de 41 7e a6 8f 08 d5 59  61 25 22 ff 3a 70 e3 91  |.A~....Ya%".:p..|
00000120  ad 04 d0 33 e4 14 85 3e  c2 02 17 ea fe 6b 59 c6  |...3...>.....kY.|
00000130  9d f4 9d b1 83 2c 6d b3  ef f9 3d 32 5b f7 6e af  |.....,m...=2[.n.|
00000140  37 df 2d 7d 36 32 74 99  8b d6 2c f1 14 cb 78 e4  |7.-}62t...,...x.|
00000150  7d 4b d1 ac ca 64 80 44  e8 b9 4f bb 7a 16 fe 37  |}K...d.D..O.z..7|
00000160  a0 62 52 de 09 8c 24 d0  c4 62 c1 1d 7d 2c f2 07  |.bR...$..b..},..|
00000170  5c a1 62 4f a9 a2 5e 9d  ed 22 6c 43 0b 58 c6 65  |\.bO..^.."lC.X.e|
00000180  0f f9 a5 31 a0 cd 6d cd  70 e2 bb 82 b7 b6 32 07  |...1..m.p.....2.|
00000190  d6 c9 53 ce 91 1b 94 b5  c9 e6 48 6f 1b 65 98 95  |..S.......Ho.e..|
000001a0  9f 03 0b 07 fb 1e a7 fb  63 19 1d a3 26 b6 1e 5e  |........c...&..^|
000001b0  b5 91 3e ef 1b 0b 1f d3  2d 68 48 1b db 15 00 fe  |..>.....-hH.....|
000001c0  ff ff 82 fe ff ff 02 20  44 01 00 f0 0d 00 00 fe  |....... D.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 28 36 01 00 00  |...........(6...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by slick666 on 2011-05-25
One things that strikes me as odd is that on both hard drives you seem to have an NTFS partition. Are you trying to have windows on one drive and Ubuntu on another? If not what is the purpose of the second drive?

---

### Post by neomaxin on 2011-05-25
First off thanks for your reply, the first drive has both the OS's XP and Ubuntu the second drive just holds data.

---

### Post by neomaxin on 2011-05-25
forgot to sat have already tried fixboot from xp recovery console and it didnt fix the problem

---

