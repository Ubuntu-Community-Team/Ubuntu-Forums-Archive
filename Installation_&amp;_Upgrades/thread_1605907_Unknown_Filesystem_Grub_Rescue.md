---
title: "Unknown Filesystem Grub Rescue"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by kingsley404 on 2010-10-25
Im fairly new to linux and my laptop froze so i rebooted it and now i have this error i have tried to load the files needed using the prompt but nothing seems to work so here is my bootinfoscript thing. 
 If no one knows a solution is there a way for me to reinstall ubuntu over the sda5 partion but keep my files?



Please help and thank you in advance also sorry if what i said made no sense im just kinda pissed lol

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,782,848   493,746,835   468,963,988   7 HPFS/NTFS
/dev/sda4         493,748,222   625,141,759   131,393,538   5 Extended
/dev/sda5         493,748,224   561,119,415    67,371,192  83 Linux
/dev/sda6         561,121,280   617,181,183    56,059,904  83 Linux
/dev/sda7         617,183,232   619,689,983     2,506,752  82 Linux swap / Solaris
/dev/sda8         619,692,032   625,141,759     5,449,728  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        9A1A3CAC1A3C86F3                       ntfs       SYSTEM RESERVED               
/dev/sda3        48EC4413EC43F9A8                       ntfs       KiNG                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        44794e1a-4998-4946-b629-f00d4661b91c   ext4                                     
/dev/sda6        81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc   ext4                                     
/dev/sda7        56eb04a9-4ff5-43d3-b036-7bd0b3d2fe19   swap                                     
/dev/sda8        4d08b5a6-6063-4e0c-913d-b3cefba07ec9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7460-907A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 44794e1a-4998-4946-b629-f00d4661b91c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 44794e1a-4998-4946-b629-f00d4661b91c
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 44794e1a-4998-4946-b629-f00d4661b91c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=44794e1a-4998-4946-b629-f00d4661b91c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 44794e1a-4998-4946-b629-f00d4661b91c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=44794e1a-4998-4946-b629-f00d4661b91c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 44794e1a-4998-4946-b629-f00d4661b91c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 44794e1a-4998-4946-b629-f00d4661b91c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9a1a3cac1a3c86f3
    chainloader +1
}
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sda7) (on /dev/sda7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sda7) -- recovery mode (on /dev/sda7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc ro single
    initrd /boot/initrd.img-2.6.32-22-generic
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=44794e1a-4998-4946-b629-f00d4661b91c    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda3 :
UUID=48EC4413EC43F9A8    /media/KiNG    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sda1 :
UUID=DAA41C49A41C2B11    /media/PQSERVICE    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda2 :
UUID=9A1A3CAC1A3C86F3    /media/SYSTEM_RESERVED    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda6 :
UUID=4d08b5a6-6063-4e0c-913d-b3cefba07ec9    none    swap    sw    0    0



=================== sda5: Location of files loaded by Grub: ===================


 259.4GB: boot/grub/core.img
 254.3GB: boot/grub/grub.cfg
 276.8GB: boot/initrd.img-2.6.35-22-generic
 261.4GB: boot/vmlinuz-2.6.35-22-generic
 276.8GB: initrd.img
 261.4GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sda7)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sda7) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 9a1a3cac1a3c86f3
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44794e1a-4998-4946-b629-f00d4661b91c
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=44794e1a-4998-4946-b629-f00d4661b91c ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44794e1a-4998-4946-b629-f00d4661b91c
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=44794e1a-4998-4946-b629-f00d4661b91c ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=81a84bb2-9d2a-4c91-964a-75e1bc8ff8bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=56eb04a9-4ff5-43d3-b036-7bd0b3d2fe19 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 296.0GB: boot/grub/core.img
 296.0GB: boot/grub/grub.cfg
 296.1GB: boot/initrd.img-2.6.32-22-generic
 296.0GB: boot/vmlinuz-2.6.32-22-generic
 296.1GB: initrd.img
 287.4GB: initrd.lz
 296.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 26 00 00 00  |........?...&...|
00000020  c2 9f 77 00 d9 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 7a 90 60 74 4e  4f 20 4e 41 4d 45 20 20  |..)z.`tNO NAME  |
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
00000100  7d 00 66 b8 b8 e3 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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
```

---

### Post by drs305 on 2010-10-25
kingsley404,

Welcome to Ubuntu and the Ubuntu forums.

What you posted is the boot info script itself. What we need is the contents of the RESULTS.txt file generated from running the boot info script.

Thanks.

I'll ask here before seeing the results. Is this an older computer or motherboard? One issue can be BIOS seeing far enough into a partition to find the boot files...

---

### Post by kingsley404 on 2010-10-25
Sorry, i have updated the post :) 

And no its a newer one i just bought it a few months ago.

---

### Post by drs305 on 2010-10-25
According to the script, Grub is looking for the Grub files on sda7 but the files are actually on sda5 (Ubuntu) or sda6 (Mint).

To fix this, boot the Live CD, open a terminal, and install Grub to the proper partition (pick which one from the above you want - I'll use sda5 Ubuntu but you can change it to Mint if you would like).

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note you add the partition number in the first command but NOT the second.

That should fix Grub. Reboot and see.

---

### Post by kingsley404 on 2010-10-25
Thank you that worked perfectly :)  i think i added sda5 in the second line instead of just sda.

---

### Post by drs305 on 2010-10-25
If you did you would have received a very pointed message advising you not to do that and the command would have failed. The reason is that you would be installing Grub to a partition, which is not recommended. It can be done, but you have to rerun the command and use the "--force" option.

If you think you did use the partition in the second command, you can rerun the boot info script and look at the first lines and the sda5 section to see where Grub is installed.

In any case, if everything is working to your satisfaction, you can mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post (it's reversible).

By the way, if you are into geeky stuff and don't want to see 2 Vista loaders in your menu or want to rename them, take a look at the G2 - Title Tweaks link in my signature line, Look at section 4 for hiding one of them. But again, it's pretty geeky and you may have better things (almost anything actually) to do with your time.

Happy Ubuntu-ing !

---

