---
title: "Update and then no boot"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by Bo0ddha on 2010-12-11
Running ubuntu on an external hdd.  Did a fresh install of 10.10 and then did the system updates.  After the reboot it won't boot to the usb hdd anymore.  It just goes straight to windows.

---

### Post by drs305 on 2010-12-11
The best way to set this up would be to have your system boot the external drive first. That way, if you have the Windows bootloader on your internal, you can boot directly to Windows with the external disconnected and to Ubuntu or Windows when the external drive is connected. 

To do this, boot to a LiveCD, mount your external drive, and then install grub to the external drive. Then make sure your BIOS boots the external drive first. 

If you need to know how to set this up we need some information. Run the boot info script and post the contents of RESULTS.txt:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Bo0ddha on 2010-12-11
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4110 MB, 4110417920 bytes
72 heads, 7 sectors/track, 15928 cylinders, total 8028160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *            688     8,028,159     8,027,472   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sdb2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sdb3          25,382,700   488,395,119   463,012,420   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,870,030,259 1,870,028,212   7 HPFS/NTFS
/dev/sdc2       1,898,031,104 1,902,030,847     3,999,744  82 Linux swap / Solaris
/dev/sdc3    *  1,870,030,848 1,882,030,079    11,999,232  83 Linux
/dev/sdc4       1,882,030,080 1,898,031,103    16,001,024  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3b312aae-bf92-c24d-8698-1e887998a9c3   ext2       casper-rw                     
/dev/sda1        F63F-B820                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CCECB432ECB418A2                       ntfs       PQSERVICE                     
/dev/sdb2        0C48B49A48B483CC                       ntfs       SYSTEM RESERVED               
/dev/sdb3        3ADCB680DCB635CB                       ntfs       Acer                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2EB2C52EB2C4FAFB                       ntfs       Meu                           
/dev/sdc2        27a9680a-f23f-460f-a253-0a46e96db627   swap                                     
/dev/sdc3        d011c4e3-0df1-4fa3-ae9d-90df484b8780   ext4                                     
/dev/sdc4        445ec8f5-4509-4b18-b869-e74ec5c53e1a   ext2                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc4        /media/445ec8f5-4509-4b18-b869-e74ec5c53e1a ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/Meu               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc3        /media/d011c4e3-0df1-4fa3-ae9d-90df484b8780 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdc3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set d011c4e3-0df1-4fa3-ae9d-90df484b8780
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set d011c4e3-0df1-4fa3-ae9d-90df484b8780
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set d011c4e3-0df1-4fa3-ae9d-90df484b8780
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=d011c4e3-0df1-4fa3-ae9d-90df484b8780 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set d011c4e3-0df1-4fa3-ae9d-90df484b8780
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=d011c4e3-0df1-4fa3-ae9d-90df484b8780 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set d011c4e3-0df1-4fa3-ae9d-90df484b8780
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d011c4e3-0df1-4fa3-ae9d-90df484b8780 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set d011c4e3-0df1-4fa3-ae9d-90df484b8780
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d011c4e3-0df1-4fa3-ae9d-90df484b8780 ro single 
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
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set d011c4e3-0df1-4fa3-ae9d-90df484b8780
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set d011c4e3-0df1-4fa3-ae9d-90df484b8780
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ccecb432ecb418a2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0c48b49a48b483cc
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

=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc3 during installation
UUID=d011c4e3-0df1-4fa3-ae9d-90df484b8780 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc4 during installation
UUID=445ec8f5-4509-4b18-b869-e74ec5c53e1a /home           ext2    defaults        0       2
/dev/sdc2       none            swap    sw              0       0

=================== sdc3: Location of files loaded by Grub: ===================


 958.7GB: boot/grub/core.img
 961.3GB: boot/grub/grub.cfg
 961.4GB: boot/initrd.img-2.6.35-22-generic
 961.3GB: boot/initrd.img-2.6.35-23-generic
 959.7GB: boot/vmlinuz-2.6.35-22-generic
 959.6GB: boot/vmlinuz-2.6.35-23-generic
 961.3GB: initrd.img
 961.4GB: initrd.img.old
 959.6GB: vmlinuz
 959.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 e0 02  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 b0 02 00 00  |........?.......|
00000020  50 7d 7a 00 90 1e 00 00  00 00 00 00 02 00 00 00  |P}z.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 20 b8 3f f6 4e  4f 20 4e 41 4d 45 20 20  |..) .?.NO NAME  |
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
00000100  7d 00 66 b8 e0 e7 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

Unknown BootLoader  on sdc4

00000000  00 00 01 ba 44 62 2d 82  64 b7 01 89 c3 f8 00 00  |....Db-.d.......|
00000010  01 bd 07 ec 81 80 05 21  18 8b 7f 63 82 03 00 c4  |.......!...c....|
00000020  99 fb ff f1 02 e3 a3 02  f9 f0 86 44 1b c1 c3 5d  |...........D...]|
00000030  1e c3 99 41 2c 7c d6 0b  99 3f 10 56 fb 09 ba 99  |...A,|...?.V....|
00000040  b9 02 98 55 31 d1 49 8b  d4 7b 41 b7 d9 31 d5 d1  |...U1.I..{A..1..|
00000050  3c 0f c5 1c 34 04 69 84  5a eb 39 91 f6 3e 2f 5f  |<...4.i.Z.9..>/_|
00000060  a2 b2 88 ed b4 60 38 e8  0e b4 2b dd 7d 35 ee 69  |.....`8...+.}5.i|
00000070  83 09 0f c1 2c 45 31 dd  a4 bc 10 28 02 cb e3 4c  |....,E1....(...L|
00000080  08 fd 16 b9 3f f2 56 47  08 8e f4 a3 46 f8 f2 04  |....?.VG....F...|
00000090  06 fc 4d 0e af 00 5f be  87 eb 72 9e 0b 04 02 3f  |..M..._...r....?|
000000a0  f1 82 6d c0 a0 30 86 98  44 46 9d c8 e4 05 cb 87  |..m..0..DF......|
000000b0  ce 84 c4 f8 ca f1 9e db  78 42 4c 3d e4 72 e3 91  |........xBL=.r..|
000000c0  f1 54 dc 31 20 38 b6 05  b4 1c a8 64 7e 8a fb 9f  |.T.1 8.....d~...|
000000d0  f8 8f 64 3a 29 0e dd 3c  08 0d 19 82 1b ec b6 ad  |..d:)..<........|
000000e0  68 0a 95 0b 77 9c 1a 14  30 53 70 17 27 24 92 00  |h...w...0Sp.'$..|
000000f0  00 e0 3e 6c 5b a0 c0 c0  c0 d4 18 18 18 1b ea c9  |..>l[...........|
00000100  fa 54 d2 c3 7c fa 13 e8  73 95 2a 7b 1d 33 f4 b0  |.T..|...s.*{.3..|
00000110  d2 ce 7e 99 4d 27 d4 9f  b9 86 e9 4d 76 18 5d c2  |..~.M'.....Mv.].|
00000120  6b 17 29 3e 54 ec 8a ab  8f 9e ac 2a 85 53 e8 88  |k.)>T......*.S..|
00000130  2d be 7e f6 b3 ed 6e 69  42 7f 0d 24 35 59 b3 f0  |-.~...niB..$5Y..|
00000140  9a c5 c7 df 1d 2a 7d 0a  bb 9a f5 ab 6b a6 85 fa  |.....*}.....k...|
00000150  4a ef 9f a5 a4 ec 6c 27  ee 6b 42 ae a5 fa 67 5e  |J.....l'.kB...g^|
00000160  5b d3 89 12 24 00 55 2e  88 74 77 fe f3 5f 43 e0  |[...$.U..tw.._C.|
00000170  40 0e 30 03 81 97 2a 9c  e2 1d d6 ad e5 2e de 34  |@.0...*........4|
00000180  e1 5b b3 53 c9 bd 60 04  6f e9 b0 0a 45 f4 80 12  |.[.S..`.o...E...|
00000190  6e ff f3 24 de 55 34 27  78 1c 2f 04 14 19 c1 91  |n..$.U4'x./.....|
000001a0  58 1b c9 66 2e 4b 31 8c  52 51 e4 54 41 9c 26 dc  |X..f.K1.RQ.TA.&.|
000001b0  84 b5 f2 5f 5a 4f a1 54  55 2e 88 70 77 fe f3 61  |..._ZO.TU..pw..a|
000001c0  4a 10 a0 7e e4 17 61 c9  f1 34 65 79 59 a6 00 01  |J..~..a..4eyY...|
000001d0  47 c0 e6 4e 57 f2 2d e4  1d 5d f8 bb 03 3d cb bd  |G..NW.-..]...=..|
000001e0  6d 39 b7 b9 1e b3 23 a8  61 24 73 23 00 42 cc 3d  |m9....#.a$s#.B.=|
000001f0  12 c9 a0 7d ff 27 c4 31  b5 3d 6e 62 ef de 7c 20  |...}.'.1.=nb..| |
00000200



```

What you described is what I already have done.  Grub is on the external hdd and the interal windows drive still has it's own boot loader.  What I don't understand is why after I update it won't boot from the usb hdd.  I hit f12 on boot to select the boot device and the usb hdd is not there.  I'm on my usb live right now and that showed up and booted just fine.  If I need to reinstall grub2 please point me to a guide or a post where I install it to the external hdd.


Edit:  Full results posted.  I agree with the thinking that the bios is not even seeing grub on the sdc.  I just don't know how to fix it.  It was working perfectly before that.  My bios does see the usb live I am currently using though.

---

### Post by drs305 on 2010-12-11
I am assuming you didn't post the entire contents of the RESULTS.txt, which gives us some more information we need.

But it appears Grub2 is installed on sdc's MBR and sdc3's Ubuntu partition. BIOS is most likely booting from sdb and using the Windows bootloader.

You can check by holding down the SHIFT key during boot to see if the Grub 2 menu appears but probably it won't.

Did your system boot from this device previously? Is the device listed in the BIOS boot order (it could be listed under USB or Hard Drives, depending on the BIOS). I know you say your BIOS couldn't see it when you pressed F12. The BIOS passes control to Grub, so if the BIOS isn't seeing your external drive there is a problem before Grub2 gets involved.

Please post the full contents of the RESULTS.txt. You can just edit your previous screen and then post when you have done it. There are UUIDS, drive/partition sizes, etc we need to check to give you a more complete answer.

---

### Post by Bo0ddha on 2010-12-11
Just rechecked my bios.  Order is usb then ide0.  I tried swapping usb ports, and playing around with having the pendrive and external hdd plugged in and no matter what it does not give me the option of booting from the external hdd.  Reinstall grub?

---

### Post by drs305 on 2010-12-11
Here is one guess - is your BIOS a bit old? All your Grub files are deep into the hard drive. If your BIOS is limited to 137GB it wouldn't see any of the boot files. 

You can check by entering BIOS on the initial boot and see what it reports as the drive size. If it shows approximately 135-137GB, enable the 'large drive' or equivalent option in BIOS or see if there is a BIOS update available. If this is the problem but you can't solve it via the BIOS, the other option is to create a /boot partition early in the drive.

The other thing I noticed is that Grub is seeing Windows as being on sda (hd0,1)/(hd0,2) and Linux on sdb (hd1,3). Since the UUID's appear correct the 'search' command plus the UUID in the 'linux' line should override the 'set root' line.

Let us know about the BIOS dirve limit and whether or not that might be the cause.

Added:
In response to your last post, if the above doesn't clarify things, you could install Grub on the Windows drive as well as long as your Ubuntu drive was always going to be connected. I'll wait for your response to what I wrote earlier in this post though.

---

### Post by Bo0ddha on 2010-12-11
Was working correctly before the update in this exact setup.  I had rebooted 2 or 3 times.  I'm on a new netbook that was bought about 6 months ago.  Checking the bios now will let you know results.

---

### Post by drs305 on 2010-12-11
> **Bo0ddha said:**
> Was working correctly before the update in this exact setup.  I had rebooted 2 or 3 times.  I'm on a new netbook that was bought about 6 months ago.  Checking the bios now will let you know results.

Well, unless you repartitioned that's probably not the issue then. The BIOS limitation can be insidious, as an initial install may put all the files within the limit, but an update can move some beyond that point and cause the BIOS to fail to boot. 

However, since your primary partition is so large to begin with there is little chance any of the Grub files have moved from inside to outside any existing BIOS limit unless you did a major reformatting.

---

### Post by Bo0ddha on 2010-12-11
Ok looked all over my bios and it gave no information on any drive sizes or large partition.  If I was to use a partition manager and move the ntfs partition to the end and put the linux ones at the begining that would solve the large hd problem?

---

### Post by drs305 on 2010-12-11
> **Bo0ddha said:**
> Ok looked all over my bios and it gave no information on any drive sizes or large partition.  If I was to use a partition manager and move the ntfs partition to the end and put the linux ones at the begining that would solve the large hd problem?

It would if that was the issue but I wouldn't do that yet. **Added:** Also, you state it's a fresh install but it ran previously. If it was on the same end of the drive that would support the proposition that the BIOS can see that deep into the drive.

If you could get to the grub prompt, you could try the "ls" command, then once you identify the Ubuntu partition, ls (hdX,Y)/boot/grub to see if it can see any of the files. It should be (hd2,3), but it might be (hd1,3) as well.

I think the next step would be to try a simple Grub reinstall from the LiveCD. If that doesn't work, from the same guide you can do a complete purge and reinstall using 'chroot'. One note if you do this though: Your Grub menuentries don't quite match up with the RESULTS.txt. It could be because your sda wasn't attached at the time you last updated grub. 

When you refer to the guide, you will have to mount your real Ubuntu OS. Use "sudo fdisk -l" or "sudo blkid" to identify your Ubuntu partition before you mount it. It could be sdb3 or sdc3 (or even sda3), so figure it out after you boot to the LiveCD desktop.

I'm going to be signing off soon, but try the "What Can I Try First" section, and if that doesn't work, proceed to the chroot procedure.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

I am still not sure why your system isn't recognizing the drive, and this shouldn't really be a Grub problem. However, accomplishing the steps above will ensure that you have taken the steps you can if Grub is somehow responsible.

---

### Post by Bo0ddha on 2010-12-11
Going to give it a try now.  Thanks for all the help and prompt replies.

Edit: Figured out my own questions.
Re-edit: Could not get it to work.  Decided to move the ntfs partition to the back of the drive and to just do a fresh install.  First thing I will do is then update and see what happens then.  I do have a preference question though.  It is a 1tb drive.  I have /, /home, /swap, ntfs.  Currently I have about 30gb of free space to make the linux partitions.  Is there a reason to make /home about 20gb or is it better to just fold it into the ntfs?  It seems to make more sense putting it into the ntfs so both os can see it.

---

### Post by drs305 on 2010-12-12
> **Bo0ddha said:**
> Currently I have about 30gb of free space to make the linux partitions.  Is there a reason to make /home about 20gb or is it better to just fold it into the ntfs?  It seems to make more sense putting it into the ntfs so both os can see it.

The /home has to be on a linux filesystem for permission support, so it can't be in an NTFS partition.

I have to stress though that if you were previously running an Ubuntu install at the end of the disk the 137GB limit is probably not the issue. I would at least Google your netbook brand and "137GB" or "137 GB" to see if anyone had that problem with it.

---

### Post by Bo0ddha on 2010-12-12
It worked before will get it working again.  Did the google search and did not find anything besides an article saying that before you upgrade your hd make sure it can handle it.  Not stating whether it did or not.

/home would be about 8gb.  I was asking if it would be smarter to roll the extra 20 gb into the ntfs or make the /home about 28 gb or so.  In a way it does not matter.

---

### Post by drs305 on 2010-12-12
> **Bo0ddha said:**
> It worked before will get it working again.  Did the google search and did not find anything besides an article saying that before you upgrade your hd make sure it can handle it.  Not stating whether it did or not.

/home would be about 8gb.  I was asking if it would be smarter to roll the extra 20 gb into the ntfs or make the /home about 28 gb or so.  In a way it does not matter.

The size of home depends on whether you are going to store your data in $HOME or not. I have a a separate /home (on occasion) but don't keep data files in it. I've given it only a couple of GBs. Of course, if you have a huge music collection in /home, you would need a much larger allocation. 

If the extra space was going to be mostly shared with Windows, I'd probably just include it in the NTFS partition.

---

### Post by Bo0ddha on 2010-12-12
NTFS it is.  Currently pushing the ntfs to the back and putting the extra gigs back into ntfs.  It's bee running for about 12 hours now atleast and I hope it will be done in the morning so I can install ubuntu.  Thats what I get for using a 1tb drive I guess.;)  Once I get it installed will post here and say it's working or not.  Thank you so much for your patience and help.  I've learned a lot from all of this.  I'm actually deployed right now and one of the guys here his computer's hdd crapped out and he can't reformat.  I had him go buy a usb stick and I have him running Ubuntu off of a persistent usb.  It's enough to let him watch his movies and skype with his family.  So thanks to you'r help I was able to help him.  I do have another question for him if you don't mind.  He has an external hdd that is password protected and I am unable to easily mount it.  How can this be done?  I've tried disk utility and it will not give me the option.  Is this because it's protected?

---

### Post by drs305 on 2010-12-12
> **Bo0ddha said:**
> He has an external hdd that is password protected and I am unable to easily mount it.  How can this be done?  I've tried disk utility and it will not give me the option.  Is this because it's protected?

Probably. For normal filesystems Ubuntu can mount them without designating the type, but I believe for encrypted devices the encryption type has to be part of the mounting command. Of course it would depend on what kind of encrypting it is. 

I've not used encryption so a better source of information could be obtained by Googling *mount encrypted drive* and include the encryption type if known.

---

