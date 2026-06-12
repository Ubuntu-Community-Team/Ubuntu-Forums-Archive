---
title: "GRUB not loading, cannot reinstall it"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by krytorii on 2012-01-27
I recently tried to format my entire ubuntu installation and start again. I formatted the partitions ubuntu was installed on (one for ubuntu, one for home) and ran through everything like normal. However when I turn my PC on I get a "grub rescue" prompt up, and an error message stating "Error: No such partition" (followed by it's UUID)

I tried following the steps [here ]("http://ubuntuforums.org/showthread.php?t=1581099")to purge and reinstall grub. I get to step 4, select the device but then get the following:

```

  &#9474;                                                                          &#9474;  
  &#9474; GRUB failed to install to the following devices:                         &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; /dev/sda                                                                 &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Do you want to continue anyway? If you do, your computer may not start   
  &#9474; up properly.                                                             &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Writing GRUB to boot device failed - continue?                           &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                    <Yes>                       <No>                      &#9474;  
  &#9474;                                                                          &#9474;  
 
```Here is the result of fdisk -l, as it seems to be the first thing asked for on all the similar threads I found.

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    12579839     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *    12579840   154839039    71129600    7  HPFS/NTFS/exFAT
/dev/sda3       154841086   390721535   117940225    5  Extended
/dev/sda5       154841088   175321087    10240000   83  Linux
/dev/sda6       388673536   390721535     1024000   82  Linux swap / Solaris
/dev/sda7       236765184   388671487    75953152    7  HPFS/NTFS/exFAT
/dev/sda8       175323136   236763135    30720000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   156248063    78123008    7  HPFS/NTFS/exFAT
```Any ideas on how to revert grub?

---

### Post by Rubi1200 on 2012-01-28
Please post the results of the boot info script so we can get a better overview of the situation.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by krytorii on 2012-02-05
Sorry it took so long to reply. The results are:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr /wubildr.mbr 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    12,579,839    12,579,777   c W95 FAT32 (LBA)
/dev/sda2    *     12,579,840   154,839,039   142,259,200   7 NTFS / exFAT / HPFS
/dev/sda3         154,841,086   390,721,535   235,880,450   5 Extended
/dev/sda5         154,841,088   175,321,087    20,480,000  83 Linux
/dev/sda6         388,673,536   390,721,535     2,048,000  82 Linux swap / Solaris
/dev/sda7         236,765,184   388,671,487   151,906,304   7 NTFS / exFAT / HPFS
/dev/sda8         175,323,136   236,763,135    61,440,000  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   156,248,063   156,246,016   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4397-A934                              vfat       PRESARIO_RP
/dev/sda2        5A701CE4701CC921                       ntfs       PRESARIO
/dev/sda5        5ac818c1-debf-4e39-8afb-02d2d7925ad7   ext4       
/dev/sda6        38b02b59-2b55-405e-989d-558c1e0aedf6   swap       
/dev/sda7        7A600F41315D0B4A                       ntfs       
/dev/sda8        68a03885-0150-46d5-8c86-3eee9dc486ea   ext4       
/dev/sdb1        7DCF87A60A66B53A                       ntfs       80GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set=root 5ac818c1-debf-4e39-8afb-02d2d7925ad7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 5ac818c1-debf-4e39-8afb-02d2d7925ad7
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ac818c1-debf-4e39-8afb-02d2d7925ad7
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5ac818c1-debf-4e39-8afb-02d2d7925ad7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ac818c1-debf-4e39-8afb-02d2d7925ad7
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5ac818c1-debf-4e39-8afb-02d2d7925ad7 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ac818c1-debf-4e39-8afb-02d2d7925ad7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ac818c1-debf-4e39-8afb-02d2d7925ad7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 5A701CE4701CC921
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
UUID=5ac818c1-debf-4e39-8afb-02d2d7925ad7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=68a03885-0150-46d5-8c86-3eee9dc486ea /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=38b02b59-2b55-405e-989d-558c1e0aedf6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 f0 00 3f 00 00 00  |........?...?...|
00000020  c1 f3 bf 00 00 30 00 00  00 00 00 00 02 00 00 00  |.....0..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 34 a9 97 43 4e  4f 20 4e 41 4d 45 20 20  |..)4..CNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda3

00000000  3b 8c f5 ac 5d 8f 01 b5  ce b0 9e 7c 8c 07 15 07  |;...]......|....|
00000010  a1 4a b2 f5 a3 ea 8a 3e  f4 f8 dc e9 e4 d3 5e 05  |.J.....>......^.|
00000020  8e b8 82 e1 11 8a c5 3f  b9 95 d2 4d e3 81 87 b2  |.......?...M....|
00000030  0c e5 7f ea 9e 93 e7 7c  c8 06 be 85 e1 0f f6 b5  |.......|........|
00000040  1b 6d 68 c9 c9 fe 0b c2  ac e5 85 7a aa e7 f5 54  |.mh........z...T|
00000050  96 be ec 49 3b 9a 92 86  50 4c 51 e9 33 10 f3 88  |...I;...PLQ.3...|
00000060  3f 07 97 f8 64 c4 85 33  22 72 a3 aa f5 c3 ba 83  |?...d..3"r......|
00000070  0d 68 b6 6f 49 23 cd 71  5d b9 cc c2 70 35 1b ac  |.h.oI#.q]...p5..|
00000080  96 4c ae ab f2 03 55 d7  67 7d 64 8b 54 e9 7a 55  |.L....U.g}d.T.zU|
00000090  5e 8e 0b 2c f6 7c 80 aa  db 91 8f b6 18 62 4c 35  |^..,.|.......bL5|
000000a0  af 2a 63 55 23 b2 13 0e  c9 45 3d fe a3 d2 b9 ee  |.*cU#....E=.....|
000000b0  bd 21 ca 24 f2 a3 0f 94  66 e6 97 1f 0d 31 42 79  |.!.$....f....1By|
000000c0  64 2e 97 a1 3d 6b b1 49  9d bd 34 76 c7 54 7d 34  |d...=k.I..4v.T}4|
000000d0  fa 27 a8 ee 35 61 1a 03  2b 90 63 9c d5 95 e4 08  |.'..5a..+.c.....|
000000e0  e5 19 ec 20 c5 91 79 6e  2d 2a 3d 1f 30 e7 9d 33  |... ..yn-*=.0..3|
000000f0  92 ce 2b 7e 4b 66 67 d5  f9 07 e9 4a 08 b5 4b 95  |..+~Kfg....J..K.|
00000100  a4 43 b4 f2 9c 1d 29 2c  6a ba 56 49 81 d2 4e 88  |.C....),j.VI..N.|
00000110  b6 07 d0 c6 f6 a2 3d fb  ac f8 1d 16 92 97 5c 84  |......=.......\.|
00000120  76 2f 21 65 a4 85 54 74  32 a5 bf 48 eb 0c 3e de  |v/!e..Tt2..H..>.|
00000130  55 de 4e 2f 58 79 99 a5  a2 cd f9 8d 65 5c 94 68  |U.N/Xy......e\.h|
00000140  11 ce 05 fc 5a ee 34 72  db 8d e6 fc 19 55 da fe  |....Z.4r.....U..|
00000150  bf ef 65 db 07 f8 db 3e  f3 37 6e bb fd a6 6d 6f  |..e....>.7n...mo|
00000160  5d 1e 1b d4 f6 31 bf e9  6d 8f 86 c6 61 01 b3 8b  |]....1..m...a...|
00000170  a9 e2 45 64 00 c3 96 60  2e e9 53 6c 4a b9 90 03  |..Ed...`..SlJ...|
00000180  19 e2 9c 84 a6 75 d8 10  bc 53 59 f1 de 22 9a aa  |.....u...SY.."..|
00000190  06 1d 33 e8 61 66 4e 8b  7f 7f e5 26 ed 36 dc b4  |..3.afN....&.6..|
000001a0  d7 ce 1a e5 ab c8 4f 9f  5e a3 33 1c 0a 71 62 dc  |......O.^.3..qb.|
000001b0  73 47 ad b4 ec 7f 71 e8  66 5c bc 2e 97 e2 00 ef  |sG....q.f\......|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 80 38 01 00 ef  |............8...|
000001d0  ff ff 05 ef ff ff 02 f8  ef 0d 00 48 1f 00 00 00  |...........H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by oldfred on 2012-02-06
Version 60 of boot script and new grub 1.99 do not show exactly which partition you are trying to boot from. 

Boot repair has a way to fix most issues and now runs the git/test version of boot script that has some fixes.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

You can manually reinstall grub2's boot loader from liveCD:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Your windows still has [COLOR=Blue]wubi[/COLOR] and what looks like a try to install [COLOR=Red]grub[/COLOR] to the Windows partition.

>     Boot files:        /boot.ini /ntldr /NTDETECT.COM [COLOR=Blue]/wubildr /wubildr.mbr [/COLOR]
                      [COLOR=Red] /boot/grub/core.img[/COLOR]


If you have nothing in wubi you can delete it and should delete the /boot/grub/core.img and related grub folders.

---

