---
title: "error:file not found grub rescue&gt; and then kernel panic"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by milstn on 2011-05-01
Hi all,
I was running ubuntu 10.10 from a previous upgrade and i decided to perform a clean install this time with natty. after  a successful install from live usb i get at reboot :
error: file not found
grub rescue>
i used the chroot method to install grub on my sda and at reboot in recovery mode i have this msg :
VFS: cannot open root device or unknown block(0,0).......please append a correct root boot option
here is my bootscriptinfo result file :
any help is appreciated. 
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ufs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    18,434,047    18,432,000  27 Hidden HPFS/NTFS
/dev/sda2          18,434,048   211,804,159   193,370,112   7 HPFS/NTFS
/dev/sda3         211,804,173   273,393,791    61,589,619  a5 FreeBSD
/dev/sda4         273,394,231   625,137,344   351,743,114   f W95 Ext d (LBA)
/dev/sda5         273,394,233   312,456,732    39,062,500  83 Linux
/dev/sda6         376,901,028   378,844,829     1,943,802  82 Linux swap / Solaris
/dev/sda7         378,844,893   460,936,979    82,092,087  83 Linux
/dev/sda8         460,937,043   625,137,344   164,200,302   7 HPFS/NTFS
/dev/sda9         312,457,216   376,899,583    64,442,368  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,849,447     7,849,386   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7CFED260FED2126E                       ntfs       WinRE                         
/dev/sda2        0A4ED4E84ED4CE17                       ntfs       SYSTEM                        
/dev/sda3                                               ufs                                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        654179de-89ca-4aab-b8c8-7ffe6c40aaaa   ext4                                     
/dev/sda6        ad0aaf07-72bd-4047-8744-26db313f113c   swap                                     
/dev/sda7        93923967-14cc-4843-8d89-9a369257f9fa   ext4                                     
/dev/sda8        01C97ED6647F1140                       ntfs                                     
/dev/sda9        795caf83-eb7c-46c8-9cd8-829650089b1e   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        45B5-3ABB                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 654179de-89ca-4aab-b8c8-7ffe6c40aaaa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 654179de-89ca-4aab-b8c8-7ffe6c40aaaa
set locale_dir=($root)/boot/grub/locale
set lang=fr_FR
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 654179de-89ca-4aab-b8c8-7ffe6c40aaaa
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro   quiet splash vt.handoff=7
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 654179de-89ca-4aab-b8c8-7ffe6c40aaaa
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro single 
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 654179de-89ca-4aab-b8c8-7ffe6c40aaaa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 654179de-89ca-4aab-b8c8-7ffe6c40aaaa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 7CFED260FED2126E
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 0A4ED4E84ED4CE17
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=654179de-89ca-4aab-b8c8-7ffe6c40aaaa /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=795caf83-eb7c-46c8-9cd8-829650089b1e /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=ad0aaf07-72bd-4047-8744-26db313f113c none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 146.6GB: boot/grub/core.img
 146.6GB: boot/grub/grub.cfg
 146.6GB: boot/vmlinuz-2.6.38-8-generic
 146.6GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb 3c 00 00 00 00 00 00  00 00 00 00 02 00 00 00  |.<..............|
00000010  00 00 00 00 00 00 00 00  12 00 02 00 00 00 00 00  |................|
00000020  00 00 00 00 00 16 1f 66  6a 00 51 50 06 53 31 c0  |.......fj.QP.S1.|
00000030  88 f0 50 6a 10 89 e5 e8  c0 00 8d 66 10 cb fc 31  |..Pj.......f...1|
00000040  c9 8e c1 8e d9 8e d1 bc  00 7c 89 e6 bf 00 07 fe  |.........|......|
00000050  c5 f3 a5 be ee 7d 80 fa  80 72 2c b6 01 e8 60 00  |.....}...r,...`.|
00000060  b9 01 00 be be 8d b6 01  80 7c 04 a5 75 07 e3 19  |.........|..u...|
00000070  f6 04 80 75 14 83 c6 10  fe c6 80 fe 05 72 e9 49  |...u.........r.I|
00000080  e3 e1 be a2 7d eb 4b 31  d2 89 16 00 09 b6 10 e8  |....}.K1........|
00000090  2e 00 bb 00 90 8b 77 0a  01 de bf 00 c0 b9 00 ae  |......w.........|
000000a0  29 f1 f3 a4 fa 49 74 14  e4 64 a8 02 75 f7 b0 d1  |)....It..d..u...|
000000b0  e6 64 e4 64 a8 02 75 fa  b0 df e6 60 fb e9 50 13  |.d.d..u....`..P.|
000000c0  bb 00 8c 8b 44 08 8b 4c  0a 0e e8 5a ff 73 2a be  |....D..L...Z.s*.|
000000d0  9d 7d e8 1c 00 be a7 7d  e8 16 00 30 e4 cd 16 c7  |.}.....}...0....|
000000e0  06 72 04 34 12 ea 00 00  ff ff bb 07 00 b4 0e cd  |.r.4............|
000000f0  10 ac 84 c0 75 f4 b4 01  f9 c3 2e f6 06 b0 08 80  |....u...........|
00000100  74 22 80 fa 80 72 1d bb  aa 55 52 b4 41 cd 13 5a  |t"...r...UR.A..Z|
00000110  72 12 81 fb 55 aa 75 0c  f6 c1 01 74 07 89 ee b4  |r...U.u....t....|
00000120  42 cd 13 c3 52 b4 08 cd  13 88 f5 5a 72 cb 80 e1  |B...R......Zr...|
00000130  3f 74 c3 fa 66 8b 46 08  52 66 0f b6 d9 66 31 d2  |?t..f.F.Rf...f1.|
00000140  66 f7 f3 88 eb 88 d5 43  30 d2 66 f7 f3 88 d7 5a  |f......C0.f....Z|
00000150  66 3d ff 03 00 00 fb 77  9d 86 c4 c0 c8 02 08 e8  |f=.....w........|
00000160  40 91 88 fe 28 e0 8a 66  02 38 e0 72 02 b0 01 bf  |@...(..f.8.r....|
00000170  05 00 c4 5e 04 50 b4 02  cd 13 5b 73 0a 4f 74 1c  |...^.P....[s.Ot.|
00000180  30 e4 cd 13 93 eb eb 0f  b6 c3 01 46 08 73 03 ff  |0..........F.s..|
00000190  46 0a d0 e3 00 5e 05 28  46 02 77 88 c3 52 65 61  |F....^.(F.w..Rea|
000001a0  64 00 42 6f 6f 74 00 20  65 72 72 6f 72 0d 0a 00  |d.Boot. error...|
000001b0  80 90 90 90 90 90 90 90  90 90 90 90 90 90 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  01 00 a5 fe ff ff 00 00  00 00 50 c3 00 00 55 aa  |..........P...U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7c 00 00 00 00 00  |........>.|.....|
00000020  aa c5 77 00 e8 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 bb 3a b5 45 20  20 20 20 20 20 20 20 20  |..).:.E         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 20 0d 16 00  66 ba 00 00 00 00 bb 00  |}.f. ...f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e dd ca 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

