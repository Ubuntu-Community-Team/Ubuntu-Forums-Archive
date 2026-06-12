---
title: "strange GRUB problem since upgrading to 11.04"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by wal3 on 2011-05-13
Hello,

since I upgraded to 11.04 from 10.10 I have a strange problem with GRUB. On first boot, it keeps hanging on "Initial Ram Disk". Then I press CTRL+ALT+DEL and at second boot, it boots up normally. It is always the same procedure: 1. boot -> hang, 2. boot -> all ok.

What could be the problem? It is definitely no hardware error. It all worked fine with 10.10.

Linux localhost 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux

grub-common                           1.99~rc1-13ubuntu3
grub-gfxpayload-lists                 0.2
grub-pc                               1.99~rc1-13ubuntu3 

menuentry 'Ubuntu, mit Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
        linux   /vmlinuz-2.6.38-8-generic root=/dev/mapper/sda5_crypt ro   noplymouth splash vt.handoff=7
        initrd  /initrd.img-2.6.38-8-generic
}

---

### Post by Hedgehog1 on 2011-05-13
Someone had this same style of issue last week.  In his case, he had two different partitions with the same UUID.

If you would do this from a boot that gets you into Ubuntu, please -

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by wal3 on 2011-05-13
#
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks for b7syn.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda4: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unbekannter Dateisystemtyp „crypto_LUKS“

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unbekannter Dateisystemtyp „crypto_LUKS“
mount: unbekannter Dateisystemtyp „crypto_LUKS“

sdb6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unbekannter Dateisystemtyp „crypto_LUKS“
mount: unbekannter Dateisystemtyp „crypto_LUKS“
mount: unbekannter Dateisystemtyp „“

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   746,551,295   746,344,448   7 HPFS/NTFS
/dev/sda3         951,351,296   976,771,071    25,419,776   7 HPFS/NTFS
/dev/sda4         746,556,615   951,337,169   204,780,555  83 Linux


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       385,559       385,497  83 Linux
/dev/sdb2             385,560   781,642,574   781,257,015   5 Extended
/dev/sdb5           1,381,653   781,642,574   780,260,922  83 Linux
/dev/sdb6             385,686     1,381,589       995,904  83 Linux


Drive: sdc ___________________ _____________________________________________________

Platte /dev/sdc: 7948 MByte, 7948206080 Byte
81 Köpfe, 10 Sektoren/Spur, 19165 Zylinder, zusammen 15523840 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,192    15,523,839    15,515,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/sda5_crypt c5146798-cb83-4317-87f2-ea9107479329   ext3                                     
/dev/mapper/sda6_crypt 10119199-81dc-4434-b74c-8e9aba183218   swap                                     
/dev/sda1        D658AED058AEAEA5                       ntfs       SYSTEM                        
/dev/sda2        F6B054EDB054B5B9                       ntfs       COMPAQ                        
/dev/sda3        1E28AA6F28AA459D                       ntfs       FACTORY_IMAGE                 
/dev/sda4        be47c095-0dfc-412f-b363-bea5d001fe0e   crypto_LUKS                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8d3e648a-983d-4d69-aa3c-83798ec4683f   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        8dc30fea-2893-414f-a42c-3de06e2c8a95   crypto_LUKS                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3431-6161                              vfat                                     
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
sda5_crypt
sda6_crypt

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/sda5_crypt /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /boot                    ext3       (rw,commit=0)
/dev/sdc1        /media/3431-6161         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sdb1/grub/grub.cfg: =============================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
set locale_dir=($root)/grub/locale
set lang=de_DE
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
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    linux    /vmlinuz-2.6.38-8-generic root=/dev/mapper/sda5_crypt ro   noplymouth splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=/dev/mapper/sda5_crypt ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, mit Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    linux    /vmlinuz-2.6.35-25-generic root=/dev/mapper/sda5_crypt ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, mit Linux 2.6.35-25-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /vmlinuz-2.6.35-25-generic root=/dev/mapper/sda5_crypt ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, mit Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    linux    /vmlinuz-2.6.35-24-generic root=/dev/mapper/sda5_crypt ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, mit Linux 2.6.35-24-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=/dev/mapper/sda5_crypt ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    linux    /vmlinuz-2.6.32-24-generic root=/dev/mapper/sda5_crypt ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-24-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=/dev/mapper/sda5_crypt ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 8d3e648a-983d-4d69-aa3c-83798ec4683f
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root D658AED058AEAEA5
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 1E28AA6F28AA459D
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

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-24-generic
    .1GB: initrd.img-2.6.35-24-generic
    .1GB: initrd.img-2.6.35-25-generic
    .0GB: initrd.img-2.6.38-8-generic
    .1GB: vmlinuz-2.6.32-24-generic
    .0GB: vmlinuz-2.6.35-24-generic
    .0GB: vmlinuz-2.6.35-25-generic
    .0GB: vmlinuz-2.6.38-8-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  ac 96 5e 5b a6 5f 7f 16  6c 25 72 d1 f9 c7 67 45  |..^[._..l%r...gE|
00000080  60 52 c5 9d 14 4c 06 47  0f 05 a5 bb 08 69 df 34  |`R...L.G.....i.4|
00000090  06 bf ab f4 7a 0b d1 5c  09 47 dd f0 42 56 a9 4c  |....z..\.G..BV.L|
000000a0  90 eb 32 c7 00 00 00 0a  62 65 34 37 63 30 39 35  |..2.....be47c095|
000000b0  2d 30 64 66 63 2d 34 31  32 66 2d 62 33 36 33 2d  |-0dfc-412f-b363-|
000000c0  62 65 61 35 64 30 30 31  66 65 30 65 00 00 00 00  |bea5d001fe0e....|
000000d0  00 ac 71 f3 00 01 f8 15  43 46 ea 13 6c 19 8a 7e  |..q.....CF..l..~|
000000e0  1b 61 c0 bb 45 53 e7 1a  75 26 39 ef d1 da aa 3a  |.a..ES..u&9....:|
000000f0  0b a4 fb f8 f6 5a 04 3f  00 00 00 08 00 00 0f a0  |.....Z.?........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdb1

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 0b 04 05 00  |................|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb5

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  f4 03 0e f4 da 03 bb 93  02 aa 56 28 74 1b b1 61  |..........V(t..a|
00000080  f6 0d a6 59 54 ab 6e 35  ae 7a b9 b4 e2 f0 e6 c4  |...YT.n5.z......|
00000090  42 40 47 57 09 5e df d0  8b 56 89 07 cf a3 74 c7  |B@GW.^...V....t.|
000000a0  58 80 d7 ab 00 00 00 0a  38 64 63 33 30 66 65 61  |X.......8dc30fea|
000000b0  2d 32 38 39 33 2d 34 31  34 66 2d 61 34 32 63 2d  |-2893-414f-a42c-|
000000c0  33 64 65 30 36 65 32 63  38 61 39 35 00 00 00 00  |3de06e2c8a95....|
000000d0  00 ac 71 f3 00 02 08 ea  d4 57 74 ae 69 3a b8 d2  |..q......Wt.i:..|
000000e0  60 29 47 35 b0 56 a8 18  f4 7d 96 29 17 7c 7c 15  |`)G5.V...}.).||.|
000000f0  44 bc 29 bc 7c cd fc b7  00 00 00 08 00 00 0f a0  |D.).|...........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdb6

00000000  f1 e3 b5 8d d8 ea b3 24  a3 03 4a b7 ff 0d 5b fd  |.......$..J...[.|
00000010  fd 1a 21 68 a6 03 70 b8  c2 2d f2 87 a9 4f eb ed  |..!h..p..-...O..|
00000020  04 0a 10 df a7 01 d6 dd  94 bf 08 ec df 27 87 9f  |.............'..|
00000030  2b 4a 06 e5 3c f1 ff 11  ac 43 ee 7d 1f 65 77 1f  |+J..<....C.}.ew.|
00000040  20 89 f6 ca 6b 2d 4d 94  3b 8f 2f 2a 3a 86 f1 6d  | ...k-M.;./*:..m|
00000050  c8 a5 7f 58 c8 b5 25 d4  2d 9b 59 0c c2 b1 8f b7  |...X..%.-.Y.....|
00000060  2b 52 b5 c1 59 68 9e 9e  d0 fc e6 a4 72 c3 59 26  |+R..Yh......r.Y&|
00000070  1b c0 f0 9a 86 6e 4f ab  66 72 f2 ea e7 1d 1c 33  |.....nO.fr.....3|
00000080  7e e8 3f 2f f9 19 a1 9e  f6 75 6b 47 c9 c1 ac 7c  |~.?/.....ukG...||
00000090  a8 8a 24 01 34 a4 14 a5  f3 2e 07 e3 3c 3e 65 81  |..$.4.......<>e.|
000000a0  ed 8a 23 93 fd d7 25 0b  3a 77 d7 5b 8b a7 ed f7  |..#...%.:w.[....|
000000b0  fb 4a 12 df 3a 25 95 21  55 ca 41 79 58 b0 2a 19  |.J..:%.!U.AyX.*.|
000000c0  0a d6 3d 48 47 35 0a f6  b0 c8 a7 73 07 cc 7d 27  |..=HG5.....s..}'|
000000d0  27 3b 7f 8f 86 f1 15 41  fb 4f 52 76 09 35 18 83  |';.....A.ORv.5..|
000000e0  8c 28 e8 f0 2f 35 94 3d  3f c9 2e d8 0f 8f a9 82  |.(../5.=?.......|
000000f0  32 82 ed 96 0d 26 5c 04  27 9a b2 c1 8d 75 21 16  |2....&\.'....u!.|
00000100  6f 7a a1 ff d8 4f 9b 90  eb e4 e0 f3 06 8f c8 a8  |oz...O..........|
00000110  0c 0e f1 8a 74 82 bd 67  45 4b cd d6 cf d9 df 0d  |....t..gEK......|
00000120  cb 4f 04 b1 4a 5c 5d 6d  93 72 e6 49 ae 82 85 1a  |.O..J\]m.r.I....|
00000130  7f 1e b8 37 e0 d5 ed db  24 e4 80 b1 ac a3 b8 72  |...7....$......r|
00000140  47 34 5d 25 0c 20 bd eb  de f5 0e f1 76 35 72 c4  |G4]%. ......v5r.|
00000150  b0 4c f6 d1 a3 b2 5c b5  82 07 cb 4b 40 ff 5b 91  |.L....\....K@.[.|
00000160  fa 20 28 72 2c 8a 29 64  85 20 2e 53 85 62 54 7d  |. (r,.)d. .S.bT}|
00000170  65 39 be 8b 3d 07 bc 48  9d 1f e5 57 5d bd 7b 5e  |e9..=..H...W].{^|
00000180  95 04 c9 a1 9e d4 e8 d7  5c 44 89 94 7b 92 a0 c4  |........\D..{...|
00000190  f1 20 c9 9f e0 a9 ac 7a  27 28 42 cf 05 f4 83 53  |. .....z'(B....S|
000001a0  ea 98 5e a1 18 ef 7e c7  a2 d7 8b 4d 88 6b 7d 9e  |..^...~....M.k}.|
000001b0  6e 00 8f 4f 70 fb 32 57  82 80 06 3e 9b 1e 70 b6  |n..Op.2W...>..p.|
000001c0  a6 a9 26 09 dd f9 23 a6  0b b9 63 95 d6 ac db e0  |..&...#...c.....|
000001d0  9d 3b e3 79 89 89 21 10  a5 27 15 e1 cc 81 dd 56  |.;.y..!..'.....V|
000001e0  91 9b 37 14 8a 7b c6 d9  0b c3 a7 76 f2 70 10 d9  |..7..{.....v.p..|
000001f0  0d 77 3d 98 be f5 b1 9e  26 ac 13 04 89 f3 33 7f  |.w=.....&.....3.|
00000200



```

---

### Post by Hedgehog1 on 2011-05-15
Greetings again!

You currently appear to have all but one of your Linux partitions encrypted:

/dev/sd**a1** - Encrypted
/dev/sd**b5** - Encrypted
/dev/sd**b6** - Encrypted

/dev/sd**b5** is presented unencrypted as:
/dev/mapper/sd**a5**_crypt c5146798-cb83-4317-87f2-ea9107479329   ext3 

/dev/sd**b6** is presented unencrypted as:        
/dev/mapper/sd**a6**_crypt 10119199-81dc-4434-b74c-8e9aba183218   swap

Your unencrypted partition is:
/dev/sdb1        8d3e648a-983d-4d69-aa3c-83798ec4683f   ext3

In grub, is is trying to boot using a mix of an unencrypted and encrypted partitions:

    search --no-floppy --fs-uuid --set=root **8d3e648a-983d-4d69-aa3c-83798ec4683f**
    linux    /vmlinuz-2.6.38-8-generic root=**/dev/mapper/sda5_crypt** ro   noplymouth splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic

It appears that here is where the difference in behavior between the old release and the new release is causing you grief; the Kernel being stored on the encrypted partition is failing to read on the first boot.

This is an area where I am out of my depth, so I am going to ask the '***grub guru***' to take a look at this and hopefully he will see a solution to this in the new release.

Please hang on while I contact him.

***The Hedge***

:KS

---

### Post by drs305 on 2011-05-15
I really don't know. I thought adding "rootdelay=60" to the linux line might allow more time for things to settle down, but I know that didn't work the last time it was tried. 

I've seen variations of this thread, and the solutions seem to be pretty obscure. I found one thread where the solution was to uninstall and reinstall a proprietary nvidia card. Go figure.

Some day I'm going to have to learn about encryption ...
and RAID ...
and Windows.

;-)

---

### Post by wal3 on 2011-05-16
Thanks for all your replies.


I did:

```

sudo apt-get --purge remove nvidia-173-modaliases nvidia-96-modaliases nvidia-common nvidia-current nvidia-glx-185 nvidia-settings

```Did not help :(

Plus I do not understand why it always work on 2nd boot attempt.

---

### Post by wal3 on 2011-05-25
No luck. Could you tell me how to **downgrade** grub to the version ubuntu 10.10 had?
I need a way to skip grub then when doing the next updates.

---

### Post by kansasnoob on 2011-05-25
> **wal3 said:**
> No luck. Could you tell me how to **downgrade** grub to the version ubuntu 10.10 had?
I need a way to skip grub then when doing the next updates.

I wrote this post for a different reason but just jump to step #3 here:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

Note: Please ignore the rest of that thread, I just used that as a placeholder for that post so I wouldn't have to copy-n-paste everything each time :)

---

