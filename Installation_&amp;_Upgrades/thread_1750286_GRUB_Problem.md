---
title: "GRUB Problem"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Lajos89 on 2011-05-05
Hello!

I've installed a linux to my second HDD and I can't boot my main OS (Windows)
Could any one help me how to fix my GRUB boot loader?

Here is my boot info result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 6.0
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       2047999999 sectors, but according to the info from 
                       fdisk, it has 3907024001 sectors.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   716,804,234   716,804,172   7 HPFS/NTFS
/dev/sda2         716,804,235   976,751,999   259,947,765   f W95 Ext d (LBA)
/dev/sda5         716,804,298   819,202,544   102,398,247   7 HPFS/NTFS
/dev/sda6         819,202,608   976,751,999   157,549,392   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   962,576,383   962,574,336  83 Linux
/dev/sdb2         962,578,430   976,771,071    14,192,642   5 Extended
/dev/sdb5         962,578,432   976,771,071    14,192,640  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 3,907,024,064 3,907,024,002  42 SFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1012 MB, 1012924416 bytes
11 heads, 42 sectors/track, 4282 cylinders, total 1978368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  64     1,978,367     1,978,304   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2CE8BA92E8BA5A32                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        84DA5012DA5002BA                       ntfs       Free                          
/dev/sda6        A250A08350A05FB1                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8050ed29-b5f3-4442-ba25-fcc41d61760d   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5                                               swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        EE4227134226E057                       ntfs                                     
/dev/sdc2        8AC420E4C420D3EB                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        D617-0C2C                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,errors=remount-ro)
/dev/sdd1        /media/usb0              vfat       (rw,noexec,nosuid,nodev,user=tamas)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional - magyar" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 8050ed29-b5f3-4442-ba25-fcc41d61760d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 8050ed29-b5f3-4442-ba25-fcc41d61760d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 8050ed29-b5f3-4442-ba25-fcc41d61760d
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8050ed29-b5f3-4442-ba25-fcc41d61760d
    echo    'Loading Linux 2.6.32-5-686 ...'
    linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=8050ed29-b5f3-4442-ba25-fcc41d61760d ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-686
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8050ed29-b5f3-4442-ba25-fcc41d61760d
    echo    'Loading Linux 2.6.32-5-686 ...'
    linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=8050ed29-b5f3-4442-ba25-fcc41d61760d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=8050ed29-b5f3-4442-ba25-fcc41d61760d /               ext3    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdd1       /media/usb0     auto    rw,user,noauto  0       0

=================== sdb1: Location of files loaded by Grub: ===================


 421.1GB: boot/grub/core.img
 421.0GB: boot/grub/grub.cfg
 421.1GB: boot/initrd.img-2.6.32-5-686
 421.0GB: boot/vmlinuz-2.6.32-5-686
 421.1GB: initrd.img
 421.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1a 7f cc e3 10 fa 27 81  4a 4b e4 10 ef c7 88 da  |......'.JK......|
00000010  76 af 7a f9 d6 eb 6f 75  34 0b 5f cb 59 4d 78 99  |v.z...ou4._.YMx.|
00000020  9c 43 6b c9 c9 e5 e2 46  8a 59 41 90 60 cf 7b cc  |.Ck....F.YA.`.{.|
00000030  46 03 2a 60 1e 02 8c 7f  8f 10 e6 ac 11 7f bb 20  |F.*`........... |
00000040  81 49 cb e4 8a 14 7e e2  b9 cd 4e 9d 39 29 04 68  |.I....~...N.9).h|
00000050  04 2e dd 3c dc d8 f7 c4  7b fc f7 eb 6f 73 ef bd  |...<....{...os..|
00000060  9a db de 66 68 46 a3 12  d7 45 30 16 09 ed 54 24  |...fhF...E0...T$|
00000070  58 31 3b 92 bc 28 7a c2  c1 78 66 f0 a7 99 64 05  |X1;..(z..xf...d.|
00000080  56 56 37 67 4c 8d 5c 21  62 60 89 c2 f0 a2 d8 68  |VV7gL.\!b`.....h|
00000090  d7 f8 27 9f ab 44 c4 e1  e1 90 b4 47 bb 84 de da  |..'..D.....G....|
000000a0  4b 36 ad a9 4f 70 56 23  d7 2b 69 d1 f0 ec 4e 84  |K6..OpV#.+i...N.|
000000b0  5b 45 03 f7 be 2f 73 e3  8d e6 5f 7d f1 8f 73 b8  |[E.../s..._}..s.|
000000c0  70 d8 55 c1 30 a8 04 0b  8c 0c 7d 1b 88 30 e2 62  |p.U.0.....}..0.b|
000000d0  bd 68 cc 67 1a 0e 5e 9d  e1 4d ac a9 93 41 c9 cf  |.h.g..^..M...A..|
000000e0  79 96 fb 77 ad e2 74 e4  fe c6 6f 79 ce 35 2f 4e  |y..w..t...oy.5/N|
000000f0  73 23 a1 e5 23 b5 7f b5  7e 10 9f 60 ae 95 e8 cf  |s#..#...~..`....|
00000100  0b f8 c1 f7 49 d9 35 e4  90 c1 36 d7 22 45 d5 0e  |....I.5...6."E..|
00000110  f4 f3 4c 2f 5e df ac 26  a9 d6 7b e3 6f 5c 2c 05  |..L/^..&..{.o\,.|
00000120  15 c4 ef 14 1b 6f 5a a8  1f 72 f6 d0 59 ae 9c f8  |.....oZ..r..Y...|
00000130  0a 63 c9 ee da ce 6a 59  13 26 30 ea d6 66 c0 79  |.c....jY.&0..f.y|
00000140  1f fe d2 37 e9 0f 29 55  7c 9e 5c b3 58 8c f4 3c  |...7..)U|.\.X..<|
00000150  7b bf bb 31 6d 50 90 d9  a5 d7 30 09 06 87 68 47  |{..1mP....0...hG|
00000160  fc ab c5 f1 ac c4 a7 95  7a 7c 2b 04 45 dd 68 5a  |........z|+.E.hZ|
00000170  3a 79 93 39 4f 3a e5 25  a7 98 de de 74 c3 3e d2  |:y.9O:.%....t.>.|
00000180  77 03 f6 35 06 29 ce c1  4c 3e 69 cb 39 a4 ff 59  |w..5.)..L>i.9..Y|
00000190  49 fd 20 c5 cb 9a 07 a9  dc e3 08 ef 12 d3 ee 63  |I. ............c|
000001a0  38 d7 4a 4d 2b ba 1e 2f  dd c5 5b dc b6 71 a7 7b  |8.JM+../..[..q.{|
000001b0  e2 6d e7 44 4f 4e e5 27  01 c2 70 2a f7 b5 00 fe  |.m.DON.'..p*....|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 27 79 1a 06 00 fe  |......?...'y....|
000001d0  ff ff 05 fe ff ff 66 79  1a 06 8f 03 64 09 00 00  |......fy....d...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  c9 a6 1e e2 b6 66 a5 5c  db 08 2d 56 74 52 fe e8  |.....f.\..-VtR..|
00000010  33 5e 13 99 23 38 25 66  a3 cb 69 d2 52 a5 5f 91  |3^..#8%f..i.R._.|
00000020  86 c6 91 0b 24 c9 76 61  73 15 25 da 97 9e 2c 5d  |....$.vas.%...,]|
00000030  51 e9 c5 a7 98 a4 7a 0e  0d b6 b5 f4 ef da 78 54  |Q.....z.......xT|
00000040  d4 db d6 0d a9 32 b6 09  ad 1b cb 11 96 54 e9 ad  |.....2.......T..|
00000050  28 48 dd 18 2a 86 f6 c0  86 32 04 65 ad 0a 7b 72  |(H..*....2.e..{r|
00000060  79 8e 4e 6a 4a 53 8d f5  ac cd b4 a1 da d1 a8 8e  |y.NjJS..........|
00000070  b7 8c be 48 ca 96 3b f1  9e 28 71 21 2e f8 e0 c3  |...H..;..(q!....|
00000080  b8 4d cc 57 15 a4 91 1b  bb 9b 86 26 c5 87 6e 5f  |.M.W.......&..n_|
00000090  f3 72 50 75 e4 c2 bb 06  1b 41 de 3a a3 9b a9 3d  |.rPu.....A.:...=|
000000a0  9f bf f4 e4 96 32 79 b8  40 96 4b 0f 23 1e aa 9a  |.....2y.@.K.#...|
000000b0  5e e7 42 a4 82 db cd 80  26 16 b5 cf 43 2d f9 81  |^.B.....&...C-..|
000000c0  71 c5 41 9e 14 a5 0a d1  23 3c a7 ec 20 6e 3f dc  |q.A.....#<.. n?.|
000000d0  fd c8 6c c8 ad a0 eb ea  9d 1a e9 6c 02 02 e7 a6  |..l........l....|
000000e0  8f 79 f5 e4 83 eb 56 53  04 e6 bc 6c f4 b2 b2 24  |.y....VS...l...$|
000000f0  6f bb 01 36 b5 bd 2a 34  85 e5 e5 9d b9 50 82 b9  |o..6..*4.....P..|
00000100  5c 59 4c a4 61 4e 4b fa  7a 0d 6e 96 de 7d bd 0c  |\YL.aNK.z.n..}..|
00000110  9c d3 de 40 d5 9a ab ad  18 c9 61 6f 63 b2 ab 28  |...@......aoc..(|
00000120  b6 58 f8 fd 7c d3 10 02  c9 71 72 e5 b9 5a 8c 53  |.X..|....qr..Z.S|
00000130  7a e1 61 85 50 8c 3c 76  98 ff f8 2a 85 e8 d1 30  |z.a.P.<v...*...0|
00000140  dd 7b 94 49 63 1f 42 ad  19 68 3d 52 eb e5 6c 29  |.{.Ic.B..h=R..l)|
00000150  1a c3 bc 3f b5 99 70 c4  e4 f1 ef 43 22 65 9a 96  |...?..p....C"e..|
00000160  55 ba 95 5e ed 91 00 df  db cc c4 26 7b 90 bc c1  |U..^.......&{...|
00000170  9f 95 8e 29 c0 8f 2e da  96 fa 9c ae 77 54 f3 be  |...)........wT..|
00000180  cf 26 2d 45 a3 19 2a b3  8f 9f 19 ba 78 04 6d 5e  |.&-E..*.....x.m^|
00000190  4a e6 a9 f5 62 8b 8b a2  70 8e 32 1b 34 4e 6f dd  |J...b...p.2.4No.|
000001a0  1e 36 d4 6e 31 96 dd f8  c9 0b ac 9e 62 20 42 de  |.6.n1.......b B.|
000001b0  43 2d f3 75 32 d9 29 72  57 cc 23 1b 37 da 00 fe  |C-.u2.)rW.#.7...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 d8 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde 
```

---

