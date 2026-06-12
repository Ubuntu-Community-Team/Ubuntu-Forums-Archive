---
title: "Reinstall Grub2 Or At Least Ubuntu"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by andrecito77 on 2011-02-06
OK I know what you are thinking. ANOTHER NOOB WHO DOESN'T USE SEARCH! Well guess what? I HAVE TRIED EVERY FRIKING THING! Sorry I am a little mad :)

#1. My boot screen was wiped out because I installed Windows 7 after Ubuntu. I tried reinstalling Grub, Grub2 etc. None of it works. I have tried everything!

#2. At least I can get my files from my home folder right? NO. After installing a bunch of crapware I finally was able to extract the root.image or something from my disks directory in Windows. But of course when I get to my home folder it gives me some crap about "not uploaded, encrypted" or whatever it is. So I find tutorials about how to decrypt your home directory from your Live CD. I tried everything. NOTHING WORKS!

#3. So at the very least can I install another Ubuntu over my old one and also keep my files? Apparently no. 

After 3 and a half hours of pointless searching and pointless terminaling I am ready to burst..... Help me for heavens sake!

Please reply ASAP I have time sensitive important files that I must recover and soon.

---

### Post by kansasnoob on 2011-02-06
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Just FYI ask before doing things like this. Doing the wrong thing only results in frustration, and sometimes worse!

---

### Post by andrecito77 on 2011-02-06
Here:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

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
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdc1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdc5 and 
                       looks at sector 741519872 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    78,153,727    77,946,880   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,156,224    78,156,162   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   665,625,489   665,623,442   7 HPFS/NTFS
/dev/sdc2         767,053,824   976,769,023   209,715,200   b W95 FAT32
/dev/sdc3         665,626,622   767,053,823   101,427,202   5 Extended
/dev/sdc5         665,626,624   762,812,415    97,185,792  83 Linux
/dev/sdc6         762,814,464   767,053,823     4,239,360  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        124C2DDA4C2DB97D                       ntfs       System Reserved               
/dev/sda2        F442FD0B42FCD37A                       ntfs       Sphire, LLC                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        701E220C22C1D023                       ntfs       Media                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C284872F848724CF                       ntfs       DSGaminator                   
/dev/sdc2        704AA5404AA50446                       ntfs       Development                   
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        92741ee5-a940-4b42-b7bc-228fc7ef328c   ext4                                     
/dev/sdc6        b6f13282-d6f3-4ebd-a526-2b8fa1533344   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    linux    /boot/vmlinuz-2.6.35-21-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    echo    'Loading Linux 2.6.35-21-generic ...'
    linux    /boot/vmlinuz-2.6.35-21-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    linux    /boot/vmlinuz-2.6.35-20-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    echo    'Loading Linux 2.6.35-20-generic ...'
    linux    /boot/vmlinuz-2.6.35-20-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 92741ee5-a940-4b42-b7bc-228fc7ef328c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 124c2dda4c2db97d
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

=============================== sdc5/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=92741ee5-a940-4b42-b7bc-228fc7ef328c /               ext4    errors=remount-ro 0       1
UUID=b6f13282-d6f3-4ebd-a526-2b8fa1533344 none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


 379.6GB: boot/grub/core.img
 350.5GB: boot/grub/grub.cfg
 379.6GB: boot/grub/stage2
 373.3GB: boot/initrd.img-2.6.35-19-generic
 342.7GB: boot/initrd.img-2.6.35-20-generic
 353.7GB: boot/initrd.img-2.6.35-21-generic
 358.3GB: boot/initrd.img-2.6.35-22-generic
 358.4GB: boot/initrd.img-2.6.35-24-generic
 379.6GB: boot/vmlinuz-2.6.35-19-generic
 379.7GB: boot/vmlinuz-2.6.35-20-generic
 379.7GB: boot/vmlinuz-2.6.35-21-generic
 379.8GB: boot/vmlinuz-2.6.35-22-generic
 379.7GB: boot/vmlinuz-2.6.35-24-generic
 358.4GB: initrd.img
 358.3GB: initrd.img.old
 379.7GB: vmlinuz
 379.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  fa fc 31 c0 8e d0 8e d8  bd 00 7c 8d 66 e0 fb b8  |..1.......|.f...|
00000010  e0 1f 8e c0 89 ee 89 ef  b9 00 01 f3 a5 ea 22 7c  |.............."||
00000020  e0 1f 8e d8 8e d0 31 c0  8e c0 8d be be 01 f6 05  |......1.........|
00000030  80 75 71 81 c7 10 00 81  ff fe 7d 72 f1 e8 c7 00  |.uq.......}r....|
00000040  6e 6f 20 61 63 74 69 76  65 20 70 61 72 74 69 74  |no active partit|
00000050  69 6f 6e 20 66 6f 75 6e  64 00 e9 fd ff e8 a7 00  |ion found.......|
00000060  72 65 61 64 20 65 72 72  6f 72 20 77 68 69 6c 65  |read error while|
00000070  20 72 65 61 64 69 6e 67  20 64 72 69 76 65 00 e9  | reading drive..|
00000080  d8 ff e8 82 00 70 61 72  74 69 74 69 6f 6e 20 73  |.....partition s|
00000090  69 67 6e 61 74 75 72 65  20 21 3d 20 35 35 41 41  |ignature != 55AA|
000000a0  00 e9 b6 ff e8 10 00 72  b4 26 81 3e fe 7d 55 aa  |.......r.&.>.}U.|
000000b0  75 d0 ea 00 7c 00 00 bb  aa 55 b4 41 cd 13 72 32  |u...|....U.A..r2|
000000c0  81 fb 55 aa 75 2c f6 c1  01 74 27 eb 10 10 00 04  |..U.u,...t'.....|
000000d0  00 00 7c 00 00 00 00 00  00 00 00 00 00 8b 45 08  |..|...........E.|
000000e0  a3 d5 7c 8b 45 0a a3 d7  7c b8 00 42 be cd 7c cd  |..|.E...|..B..|.|
000000f0  13 c3 b8 04 02 bb 00 7c  8b 4d 02 8a 75 01 cd 13  |.......|.M..u...|
00000100  c3 31 db b4 0e cd 10 5e  ac 56 3c 00 75 f3 c3 00  |.1.....^.V<.u...|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  89 d1 d7 39 00 00 80 01  |...........9....|
000001c0  01 00 0c fe ff 00 3f 00  00 00 82 91 a8 04 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader  on sdc3

00000000  70 75 74 40 3f 24 74 69  6d 65 5f 70 75 74 40 5f  |put@?$time_put@_|
00000010  57 56 3f 24 6f 73 74 72  65 61 6d 62 75 66 5f 69  |WV?$ostreambuf_i|
00000020  74 65 72 61 74 6f 72 40  5f 57 55 3f 24 63 68 61  |terator@_WU?$cha|
00000030  72 5f 74 72 61 69 74 73  40 5f 57 40 73 74 64 40  |r_traits@_W@std@|
00000040  40 40 73 74 64 40 40 40  73 74 64 40 40 4d 42 45  |@@std@@@std@@MBE|
00000050  3f 41 56 3f 24 6f 73 74  72 65 61 6d 62 75 66 5f  |?AV?$ostreambuf_|
00000060  69 74 65 72 61 74 6f 72  40 5f 57 55 3f 24 63 68  |iterator@_WU?$ch|
00000070  61 72 5f 74 72 61 69 74  73 40 5f 57 40 73 74 64  |ar_traits@_W@std|
00000080  40 40 40 32 40 56 33 32  40 41 41 56 69 6f 73 5f  |@@@2@V32@AAVios_|
00000090  62 61 73 65 40 32 40 5f  57 50 42 55 74 6d 40 40  |base@2@_WPBUtm@@|
000000a0  44 44 40 5a 00 3f 64 6f  5f 73 63 61 6e 5f 69 73  |DD@Z.?do_scan_is|
000000b0  40 3f 24 63 74 79 70 65  40 47 40 73 74 64 40 40  |@?$ctype@G@std@@|
000000c0  4d 42 45 50 42 47 46 50  42 47 30 40 5a 00 3f 64  |MBEPBGFPBG0@Z.?d|
000000d0  6f 5f 73 63 61 6e 5f 69  73 40 3f 24 63 74 79 70  |o_scan_is@?$ctyp|
000000e0  65 40 5f 57 40 73 74 64  40 40 4d 42 45 50 42 5f  |e@_W@std@@MBEPB_|
000000f0  57 46 50 42 5f 57 30 40  5a 00 3f 64 6f 5f 73 63  |WFPB_W0@Z.?do_sc|
00000100  61 6e 5f 6e 6f 74 40 3f  24 63 74 79 70 65 40 47  |an_not@?$ctype@G|
00000110  40 73 74 64 40 40 4d 42  45 50 42 47 46 50 42 47  |@std@@MBEPBGFPBG|
00000120  30 40 5a 00 3f 64 6f 5f  73 63 61 6e 5f 6e 6f 74  |0@Z.?do_scan_not|
00000130  40 3f 24 63 74 79 70 65  40 5f 57 40 73 74 64 40  |@?$ctype@_W@std@|
00000140  40 4d 42 45 50 42 5f 57  46 50 42 5f 57 30 40 5a  |@MBEPB_WFPB_W0@Z|
00000150  00 3f 64 6f 5f 74 68 6f  75 73 61 6e 64 73 5f 73  |.?do_thousands_s|
00000160  65 70 40 3f 24 5f 4d 70  75 6e 63 74 40 44 40 73  |ep@?$_Mpunct@D@s|
00000170  74 64 40 40 4d 42 45 44  58 5a 00 3f 64 6f 5f 74  |td@@MBEDXZ.?do_t|
00000180  68 6f 75 73 61 6e 64 73  5f 73 65 70 40 3f 24 5f  |housands_sep@?$_|
00000190  4d 70 75 6e 63 74 40 47  40 73 74 64 40 40 4d 42  |Mpunct@G@std@@MB|
000001a0  45 47 58 5a 00 3f 64 6f  5f 74 68 6f 75 73 61 6e  |EGXZ.?do_thousan|
000001b0  64 73 5f 73 65 70 40 3f  24 5f 4d 70 75 6e 00 fe  |ds_sep@?$_Mpun..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f0 ca 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff bd f7  ca 05 45 b0 40 00 00 00  |..........E.@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by andrecito77 on 2011-02-06
BTW: The Ubuntu directory I want is sdc5

---

### Post by kansasnoob on 2011-02-06
So, you have two 40GB drives and one 500GB drives, which drive is set as the boot drive in BIOS?

If Windows is booting sda must be the boot drive.

Can you change things in BIOS to have the 500GB drive boot first?

---

### Post by kansasnoob on 2011-02-06
> **andrecito77 said:**
> BTW: The Ubuntu directory I want is sdc5

Would it not be best to get Ubuntu booting?

---

### Post by andrecito77 on 2011-02-06
Windows is ON the 500 gb one. ^ What do you mean by that?
BTW: i'm watching the superbowl at the same time so sorry for late response...

---

### Post by kansasnoob on 2011-02-06
If you really just want your Win to be able to read the files on Ubuntu look here:

[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

But take note of the fact that they put this warning in red:

**[COLOR="Red"]Important Note:- Use these tools with your own risk if you don’t use them properly it will remove your linux partition data[/COLOR]**

I double, super duper, quadruple the warning!

---

### Post by andrecito77 on 2011-02-06
I already said I extracted the image, but it gave an encrypted thing.

---

### Post by kansasnoob on 2011-02-06
> **andrecito77 said:**
> Windows is ON the 500 gb one. ^ What do you mean by that?
BTW: i'm watching the superbowl at the same time so sorry for late response...

Yes, Win is on sdc1:

> sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

But the drive MBR's are as follows:

> => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.


So Windows is using the MBR of sda to boot! If Windows is booting OK you either need to change the boot priority in BIOS or install Ubuntu's grub2 to sda.

BTW regarding your original post/rant, and the fact that it's your first post ever, and you're so angry, and things are so urgent - following that with, soory I was watching some crap on TV is a bit of a put-off!

Kind of like the people I prepare taxes for free of charge. All they do is complain about the government and most are getting money back they never paid in :mad:

---

### Post by andrecito77 on 2011-02-06
The Superbowl is important. More important than Ubuntu :) But not getting off track, you're saying that if I change the boot order to accommodate Ubuntu it will show the boot screen?

---

### Post by presence1960 on 2011-02-06
> **kansasnoob said:**
> 

BTW regarding your original post/rant, and the fact that it's your first post ever, and you're so angry, and things are so urgent - following that with, soory I was watching some crap on TV is a bit of a put-off!

Kind of like the people I prepare taxes for free of charge. All they do is complain about the government and most are getting money back they never paid in :mad:

+1

I am laughing reading this.

---

### Post by presence1960 on 2011-02-06
> **andrecito77 said:**
> The Superbowl is important. More important than Ubuntu :) But not getting off track, you're saying that if I change the boot order to accommodate Ubuntu it will show the boot screen?

It is only a game. But since it is so important finish watching it. The forum is here 24 hours a day.

---

### Post by andrecito77 on 2011-02-06
Good to go :) Anyways I really do need to get help and soon. I need the files in there by tomorrow at 1 PM USA Central Time.

---

### Post by presence1960 on 2011-02-06
> **kansasnoob said:**
> So, you have two 40GB drives and one 500GB drives, which drive is set as the boot drive in BIOS?

If Windows is booting sda must be the boot drive.

Can you change things in BIOS to have the 500GB drive boot first?

+1

Go into BIOS and set the 500GB disk to boot first in the hard disk boot order. This will bring up GRUB menu at boot.

---

### Post by andrecito77 on 2011-02-06
Aha OK slight problem. My 500 gig drive is IDE Drive #4 (Technically #5) and it won't show up in the startup order screen thing. What can I do to make the 500 gig drive IDE Drive 0,1,2,3 or 4?

---

### Post by andrecito77 on 2011-02-07
Bump I need the info soon :(

---

### Post by oldfred on 2011-02-07
BIOS should report drives by the three sizes. If two are the same it is often difficult to tell them apart. (I just boot either until I get the results I expected).

---

### Post by andrecito77 on 2011-02-07
Done solved! I accidentally deleted the Ubuntu installation and I was barking up the wrong Ubuntu installation :) So now I have to deal with my dumbness.

---

