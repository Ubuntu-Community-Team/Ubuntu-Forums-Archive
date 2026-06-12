---
title: "Help! Grub corrupted"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by choggo123 on 2011-03-02
Hi. I think i messed up. I tried to reinstall grub 2 in order to be able to boot into ubuntu after installing Windows 7. Now all i get is this...

GNU GRUB version 1.98+20100804-5ubuntu3
Minimal Bash-like line editing is supported...

I already ran the boot-info script

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1                  63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,040    21,687,749     2,152,710  83 Linux
/dev/sda3          21,687,750   269,602,829   247,915,080   5 Extended
/dev/sda5          21,687,813    30,282,524     8,594,712  82 Linux swap / Solaris
/dev/sda6          30,282,588    30,314,654        32,067  83 Linux
/dev/sda7          30,314,718   269,602,829   239,288,112  83 Linux
/dev/sda4    *    269,602,830   312,576,704    42,973,875   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2b8a643c-1d08-b944-a1d5-3306f610d1ad   ext2       casper-rw                     
/dev/sda1        4e2fe1fe-6786-42a1-84c7-b774cb66d320   ext4                                     
/dev/sda2        2ccfb14a-0a52-430c-ad37-56eb3557a672   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        86F09ADAF09AD033                       ntfs                                     
/dev/sda5        04cb3b44-1885-4161-b3d9-f825ad25b490   swap                                     
/dev/sda7        6a68b350-1573-4c06-8cfe-6241befd2d8a   ext4       home                          
/dev/sda: PTTYPE="dos" 
/dev/sdb         1F0D-2003                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
# / was on /dev/sda1 during installation
UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=2ccfb14a-0a52-430c-ad37-56eb3557a672 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=6a68b350-1573-4c06-8cfe-6241befd2d8a /home           ext4    defaults        0       2
# /windows was on /dev/sda3 during installation
UUID=433E-832E  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=04cb3b44-1885-4161-b3d9-f825ad25b490 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img

============================= sda2/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 4e2fe1fe-6786-42a1-84c7-b774cb66d320
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    linux    /vmlinuz-2.6.35-25-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro   quiet splash
    initrd    /initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /vmlinuz-2.6.35-25-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    linux    /vmlinuz-2.6.35-24-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro   quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    linux    /vmlinuz-2.6.35-23-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro   quiet splash
    initrd    /initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /vmlinuz-2.6.35-23-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    linux    /vmlinuz-2.6.35-22-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    linux    /vmlinuz-2.6.32-25-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro   quiet splash
    initrd    /initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /vmlinuz-2.6.32-25-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    linux    /vmlinuz-2.6.31-20-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro   quiet splash
    initrd    /initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /vmlinuz-2.6.31-20-generic root=UUID=4e2fe1fe-6786-42a1-84c7-b774cb66d320 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ccfb14a-0a52-430c-ad37-56eb3557a672
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda2: Location of files loaded by Grub: ===================


  10.1GB: grub/core.img
  10.1GB: grub/grub.cfg
  10.2GB: initrd.img-2.6.31-20-generic
  10.1GB: initrd.img-2.6.32-25-generic
  10.1GB: initrd.img-2.6.35-22-generic
  10.3GB: initrd.img-2.6.35-23-generic
  10.2GB: initrd.img-2.6.35-24-generic
  10.3GB: initrd.img-2.6.35-25-generic
  10.2GB: vmlinuz-2.6.31-20-generic
  10.3GB: vmlinuz-2.6.32-25-generic
  10.3GB: vmlinuz-2.6.35-22-generic
  10.3GB: vmlinuz-2.6.35-23-generic
  10.3GB: vmlinuz-2.6.35-24-generic
  10.3GB: vmlinuz-2.6.35-25-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  ff d3 b0 d8 7b 38 3f e7  88 e7 db c9 e0 3b 17 17  |....{8?......;..|
00000010  68 c3 8d dc ae 09 08 b0  22 c1 49 fa 34 ac 2b 0a  |h.......".I.4.+.|
00000020  ac 01 41 43 3e 9d fd 73  87 ed 79 7a 7a 9f e8 35  |..AC>..s..yzz..5|
00000030  4e 34 25 65 ed 0d af 8f  b0 8a 05 2a 05 bd e7 ae  |N4%e.......*....|
00000040  e8 68 2c eb 73 bd ae dc  e3 bb bf 1a 13 cc 17 f2  |.h,.s...........|
00000050  6f 08 f4 b8 57 5b e4 4f  4b ab d2 2f d6 b8 4a 21  |o...W[.OK../..J!|
00000060  30 35 20 ee 31 4b d3 08  14 06 10 28 20 80 37 22  |05 .1K.....( .7"|
00000070  b1 73 6c f0 86 2b 17 94  60 64 65 c6 75 7b 16 76  |.sl..+..`de.u{.v|
00000080  9e 8c 8b 2c 20 f0 dc 93  25 9f 5b 49 c7 27 ec b6  |..., ...%.[I.'..|
00000090  0d 39 3c 81 59 98 1d eb  a5 ad 30 a5 af d9 97 25  |.9<.Y.....0....%|
000000a0  0c 6d 36 bb d1 49 32 6c  a4 d7 6b c3 4e b5 99 97  |.m6..I2l..k.N...|
000000b0  2b 72 39 f4 92 2f 09 d4  88 44 55 bf d2 8e d8 fc  |+r9../...DU.....|
000000c0  fe 7f e3 d3 e2 7e f6 b1  e4 dd c7 25 e1 db 47 e6  |.....~.....%..G.|
000000d0  99 dd df 1d 63 5e 60 61  da 7c 52 b5 91 b1 18 8b  |....c^`a.|R.....|
000000e0  72 42 aa 20 1e 97 06 be  d7 14 44 81 2e 63 ea 34  |rB. ......D..c.4|
000000f0  1f 6a ba 17 e0 82 ec cf  7e b2 7e dd ff 9b d1 ab  |.j......~.~.....|
00000100  b1 d8 e3 15 95 f1 7d b1  2e fe e3 4e 07 27 bd 40  |......}....N.'.@|
00000110  f7 fb 5f 7f 7a 3f 87 e2  68 8c 75 27 bb ab e0 51  |.._.z?..h.u'...Q|
00000120  ee 5f d8 53 18 17 33 0c  8c 4f 1a e7 dc 22 8a 00  |._.S..3..O..."..|
00000130  20 4c a3 4f 74 cf 0b 09  02 1b 13 f9 2e 39 8f 51  | L.Ot........9.Q|
00000140  d2 77 f9 0f 7e fd bf d0  5c a6 43 9b 7c dc 47 c4  |.w..~...\.C.|.G.|
00000150  8c 79 18 75 95 39 c8 15  1e a2 3d 95 bb 86 91 58  |.y.u.9....=....X|
00000160  c3 b5 61 44 2e 7b 29 e2  4e e3 cd 5b 1e 29 89 7b  |..aD.{).N..[.).{|
00000170  76 d5 ee 2f e0 10 b0 ad  c4 68 e8 3b 3e d7 92 5e  |v../.....h.;>..^|
00000180  39 26 1f 7f 03 18 9e 9e  ea 56 c9 06 15 5f b1 f8  |9&.......V..._..|
00000190  93 cc ef 53 81 a5 17 82  5a bb 92 83 20 1a d9 5a  |...S....Z... ..Z|
000001a0  82 70 73 94 9b 75 c3 96  c8 15 69 e3 5b 8b 80 3f  |.ps..u....i.[..?|
000001b0  0a 37 b0 23 0f 9d 86 40  9a 3e e8 5d 08 12 10 73  |.7.#...@.>.]...s|
000001c0  dd f3 f0 6b 4f 63 e0 3e  ed f2 50 8f de af 1d 4f  |...kOc.>..P....O|
000001d0  62 9a 02 d8 bc cf 93 2c  6d 98 c6 18 89 98 c9 8b  |b......,m.......|
000001e0  23 90 5c aa 30 38 61 ee  4c f0 2f 47 ef d9 2c 02  |#.\.08a.L./G..,.|
000001f0  e0 cf 62 93 d8 fb ac 27  c1 32 98 b5 1b 66 cf 3b  |..b....'.2...f.;|
00000200

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  fe 1f 3d 00 72 1e 00 00  00 00 00 00 02 00 00 00  |..=.r...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 03 20 0d 1f 4e  4f 20 4e 41 4d 45 20 20  |..). ..NO NAME  |
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
00000100  7d 00 66 b8 08 3d 00 00  66 ba 00 00 00 00 bb 00  |}.f..=..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
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


I have no idea how to recover the thing... thanks in advance!

---

### Post by ronparent on 2011-03-02
It looks like you somehow got grub installed on sda2 instead of sda1. Try the reinstall again from a live cd.

In a terminal write: > sudo mount /dev/sda1 /mnt
Then: > sudo grub-install --root-directory=/mnt/ /dev/sda

I believe that will fix you up.

---

### Post by choggo123 on 2011-03-02
Thank you for the advice. That's exactly what I tried the first time. Now I tried it again and it didn't change anything. Hm...

---

### Post by Quackers on 2011-03-02
You have a separate boot partition it seems. 
I'm not sure whether all your boot files are correct either.
I would suggest that you purge then re-install grub following the "Why chroot" section of the guide below, by drs305.
You will need to mount both your boot partition (sda2) and your root partition (sda1) first. The details of how to do that are given in the guide.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by choggo123 on 2011-03-03
Ah, that did the trick! Thanks very much! :)

Is it normal that now ubuntu can't mount the Windows partition?

---

### Post by Quackers on 2011-03-03
Glad to hear that fixed it :-)
Can you see the Windows files in Places?

---

### Post by choggo123 on 2011-03-03
I can see the Windows partition... but while booting I get something like "/windows cannot be mounted - Continue to wait; press S to skip or press M to repair manually"

Just a bit confusing...

---

### Post by Quackers on 2011-03-03
If you can see Windows in Places then it is being mounted. It may be slow to mount and that is causing the message at boot.
I don't know why that may be though.
Is it on a laptop and if so which laptop?

---

### Post by oldfred on 2011-03-03
The sda3 partition is the extended partition which is just a container for the logical partitions.  
You are trying to mount the sda3 with vfat, I do not see a FAT partition. UUID looks obsolete.
You will need to mount sda4 your windows partition. But I recommend not writing into windows system partitions as Ubuntu will show all the hidden files, lets you write files even if hibernated, and lets you accidently damage your windows. Best to set it read only and create a shared NTFS partition for any data you want in both systems.

/dev/sda3          21,687,750   269,602,829   247,915,080   5 Extended

From fstab:
# /windows was on /dev/sda3 during installation
UUID=433E-832E  /windows        vfat    utf8,umask=007,gid=46 0       1

/dev/sda4        86F09ADAF09AD033                       ntfs                                     




Shared NTFS partition 
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by choggo123 on 2011-03-05
> **oldfred said:**
> You are trying to mount the sda3 with vfat, I do not see a FAT partition. UUID looks obsolete.
You will need to mount sda4 your windows partition. But I recommend not writing into windows system partitions as Ubuntu will show all the hidden files, lets you write files even if hibernated, and lets you accidently damage your windows. Best to set it read only and create a shared NTFS partition for any data you want in both systems.


That sounds reasonable. But I have no idea of how to do that, actually...

As for the link you gave me, I'll do that when I find the time.

---

### Post by oldfred on 2011-03-05
You should edit out the incorrect line. You can delete or just put  a # at the beginning of the line to convert to a comment. That will remove the error on startup.

cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by choggo123 on 2011-03-05
Wow, thanks. Now I'm virtually problem-free. Great work, all of you.

---

