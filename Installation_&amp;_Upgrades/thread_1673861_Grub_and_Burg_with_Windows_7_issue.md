---
title: "Grub and Burg with Windows 7 issue"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by khandu on 2011-01-23
Hey Guys

I have 3 linux partitions

/
/boot
swap

Here's the story

1) was running ubuntu 10.10 64bit with burg
2) Installed windows 7.. it got removed. 
3) So boot via ubuntu usb and ran

sudo mount /dev/sda7 /mnt/home
sudo mount /dev/sda4 /mnt/boot
sudo grub-install --root-directory=/mnt/boot /dev/sda
reboot

now its stuck at grub> .. I am unable to fix this issue

How can I get my grub / burg running again with windows as option

currently to boot i do

grub> root (hd0,1)
grub> chainloader +1
grub> boot

I am sure I have grub2

---

### Post by Quackers on 2011-01-23
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by khandu on 2011-01-23
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,766,794   167,766,732   7 HPFS/NTFS
/dev/sda2         180,463,614   976,768,064   796,304,451   5 Extended
/dev/sda5         314,568,828   629,137,529   314,568,702   7 HPFS/NTFS
/dev/sda6         629,137,593   976,768,064   347,630,472   7 HPFS/NTFS
/dev/sda7         180,463,616   314,566,655   134,103,040  83 Linux
/dev/sda3         167,768,064   179,484,671    11,716,608  82 Linux swap / Solaris
/dev/sda4         179,484,672   180,461,567       976,896  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4060 MB, 4060086272 bytes
156 heads, 46 sectors/track, 1105 cylinders, total 7929856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     7,929,855     7,927,808   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7DDE858A6F9D7A6A                       ntfs       Windows 7                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        3678764b-abb9-40f4-88fe-4ce665658258   swap                                     
/dev/sda4        2a94b924-ab99-4d37-bf66-fd387dd6aad8   ext4                                     
/dev/sda5        14B4530D34B587EE                       ntfs       Downloads                     
/dev/sda6        33DD6F6D34AEFBFF                       ntfs       Misc                          
/dev/sda7        59bf5480-b807-4a4f-8aa4-13ca37ad5b45   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        98D6-61A9                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda7 :
UUID=59bf5480-b807-4a4f-8aa4-13ca37ad5b45    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda4 :
UUID=2a94b924-ab99-4d37-bf66-fd387dd6aad8    /boot    ext4    defaults    0    2
#Entry for /dev/sda1 :
UUID=7DDE858A6F9D7A6A    /media/Windows_7    ntfs-3g    defaults,locale=en_AU.utf8    0    0
#Entry for /dev/sda5 :
UUID=14B4530D34B587EE    /media/Downloads    ntfs-3g    defaults,locale=en_AU.utf8    0    0
#Entry for /dev/sda6 :
UUID=33DD6F6D34AEFBFF    /media/Misc        ntfs-3g    defaults,locale=en_AU.utf8    0    0
#Entry for /dev/sda3 :
UUID=3678764b-abb9-40f4-88fe-4ce665658258    none    swap    sw    0    0



============================= sda4/grub/grub.cfg: =============================

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
set default="6"
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 59bf5480-b807-4a4f-8aa4-13ca37ad5b45
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 2a94b924-ab99-4d37-bf66-fd387dd6aad8
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2a94b924-ab99-4d37-bf66-fd387dd6aad8
    linux    /vmlinuz-2.6.35-24-generic root=UUID=59bf5480-b807-4a4f-8aa4-13ca37ad5b45 ro  splash vga=789  quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2a94b924-ab99-4d37-bf66-fd387dd6aad8
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=59bf5480-b807-4a4f-8aa4-13ca37ad5b45 ro single  splash vga=789
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2a94b924-ab99-4d37-bf66-fd387dd6aad8
    linux    /vmlinuz-2.6.35-22-generic root=UUID=59bf5480-b807-4a4f-8aa4-13ca37ad5b45 ro  splash vga=789  quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2a94b924-ab99-4d37-bf66-fd387dd6aad8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=59bf5480-b807-4a4f-8aa4-13ca37ad5b45 ro single  splash vga=789
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2a94b924-ab99-4d37-bf66-fd387dd6aad8
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2a94b924-ab99-4d37-bf66-fd387dd6aad8
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7dde858a6f9d7a6a
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

=================== sda4: Location of files loaded by Grub: ===================


  91.9GB: boot/grub/core.img
  92.1GB: grub/core.img
  92.1GB: grub/grub.cfg
  91.9GB: initrd.img-2.6.35-22-generic
  91.9GB: initrd.img-2.6.35-24-generic
  91.9GB: vmlinuz-2.6.35-22-generic
  91.9GB: vmlinuz-2.6.35-24-generic

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

Unknown BootLoader  on sda2

00000000  7b ce b9 a2 10 80 af 61  ab de 67 34 0a d8 40 43  |{......a..g4..@C|
00000010  be 8d 94 2f ed e9 26 ca  2e 76 08 c5 74 86 29 24  |.../..&..v..t.)$|
00000020  b6 bd c6 6f 16 13 9d 05  3d 55 7b c1 c1 7e e4 c2  |...o....=U{..~..|
00000030  1e b3 06 f0 12 e2 08 c7  a8 2f 29 f8 60 58 a3 1d  |........./).`X..|
00000040  60 05 f2 b7 4b 47 0a c1  c3 ad 5e 45 df 37 1f f8  |`...KG....^E.7..|
00000050  f0 b1 1c 5b 28 6d 64 8b  0a 35 0f 21 47 53 f0 04  |...[(md..5.!GS..|
00000060  f4 13 b5 6b 8d 57 cd 3c  8a 98 9d 38 d7 bb ad 30  |...k.W.<...8...0|
00000070  3a dc 2e b4 ba 1d aa 29  3c b5 ec 27 7b ed 6e 68  |:......)<..'{.nh|
00000080  a9 6f 85 92 cd 2d 1b a1  a9 91 b5 32 8c 19 85 5b  |.o...-.....2...[|
00000090  e2 63 07 12 67 0d 2c 60  64 9e 93 9b 94 6b 7c 72  |.c..g.,`d....k|r|
000000a0  a8 75 de 8e c3 98 8a 6f  db 52 34 5a 28 18 ba f8  |.u.....o.R4Z(...|
000000b0  94 ab 5a f7 0a 80 8a dd  5a 5b eb 52 a4 07 e9 7e  |..Z.....Z[.R...~|
000000c0  4c f0 2b 05 b4 ed d4 d5  aa 3f b5 9f 77 fd 0f 94  |L.+......?..w...|
000000d0  84 b2 56 74 d1 ac 90 f4  47 58 73 c8 62 c1 71 7d  |..Vt....GXs.b.q}|
000000e0  6c 55 90 7f 75 fe ae 5d  9f 8f 28 2f eb d6 78 39  |lU..u..]..(/..x9|
000000f0  f0 54 a8 a9 d3 8e fa 3c  3b c7 be e6 5c 74 7a 0c  |.T.....<;...\tz.|
00000100  3e 83 8e 71 e3 23 85 24  fb 68 a0 78 83 73 d7 85  |>..q.#.$.h.x.s..|
00000110  43 13 c7 74 83 8a ec a5  ba 5f 33 e5 c9 aa df ef  |C..t....._3.....|
00000120  73 10 dc 3f 96 40 99 4b  71 f9 40 7b 62 17 e2 ea  |s..?.@.Kq.@{b...|
00000130  08 49 24 85 1d a9 d9 aa  6d 6e 6f e6 2f 5c 7e 39  |.I$.....mno./\~9|
00000140  b7 50 c4 ea e2 42 0b fb  1b d2 8e 1a b6 4e 64 be  |.P...B.......Nd.|
00000150  14 ee c5 6b 3f d9 b3 9a  02 af 58 90 23 bc 20 b5  |...k?.....X.#. .|
00000160  a6 7f 3f 2b 33 20 f0 01  bf 8e 77 3d 1a 9e 7a 6f  |..?+3 ....w=..zo|
00000170  12 24 6f 7c 40 dd 3f 13  89 69 4c da e1 36 ad c4  |.$o|@.?..iL..6..|
00000180  11 24 47 a1 5b a9 5d 23  27 72 6b 98 92 2a 18 d0  |.$G.[.]#'rk..*..|
00000190  bd 18 16 5f 6d 61 fd 02  1b 21 cf eb 35 29 c8 81  |..._ma...!..5)..|
000001a0  c9 63 6e ef 8c ac da 7a  81 2e 89 37 54 0e 45 b7  |.cn....z...7T.E.|
000001b0  b7 28 bf 69 82 a5 f3 ad  70 62 9c c2 52 1b 00 fe  |.(.i....pb..R...|
000001c0  ff ff 07 fe ff ff 7e 48  fe 07 fe ef bf 12 00 fe  |......~H........|
000001d0  ff ff 05 fe ff ff 7c 38  be 1a c7 6b b8 14 00 00  |......|8...k....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 a2 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 f8 78 00 2f 1e 00 00  00 00 00 00 02 00 00 00  |..x./...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 a9 61 d6 98 4e  4f 20 4e 41 4d 45 20 20  |..).a..NO NAME  |
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
00000100  7d 00 66 b8 08 40 00 00  66 ba 00 00 00 00 bb 00  |}.f..@..f.......|
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

### Post by Quackers on 2011-01-23
I would suggest booting from the live cd/usb and following the guide below to purge-re-install grub using the chroot method.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by khandu on 2011-01-23
thanks it worked.. 

so i must have done something wrong in 1st post.. i think the mounting on diff partitions instead of one inside another...

---

### Post by Quackers on 2011-01-23
You're welcome :-)
I suspect you mounted the right partitions to the wrong place.
Nevermind, all is fixed :-)
Please mark the thread as solved using the Thread Tools near the top of the page. Thanks.

---

