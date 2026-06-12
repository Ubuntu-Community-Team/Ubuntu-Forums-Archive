---
title: "Will not boot ubuntu 10.10 or win 7"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by apexracer on 2011-02-22
I have win7 installed on master hdd and did that first.  I then had Linux Mint 10 on my second hdd, then I wanted to switch to Ubuntu. I tried installing along side Mint, and it did not work. Then I just erased and formatted the Mint partitions and started a fresh ubuntu 10.10.  I went to reboot and I got nothing but a cursor in the top left corner. I have the RESULTS.txt from the the boot info script. Please help.

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 13261608 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 300512 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
45 heads, 32 sectors/track, 162806 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32   234,439,199   234,439,168   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       976,895       974,848  83 Linux
/dev/sdb2             976,896    59,570,175    58,593,280  83 Linux
/dev/sdb3          59,570,176    69,335,039     9,764,864  82 Linux swap / Solaris
/dev/sdb4          69,337,086    78,176,255     8,839,170   5 Extended
/dev/sdb5          69,337,088    78,176,255     8,839,168  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FE5083AA5083686B                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b5b9a8ef-59ee-4606-b63c-95366c4bb379   ext4                                     
/dev/sdb2        f0e01c40-738e-444a-9e79-a2c240dc73d9   ext4                                     
/dev/sdb3        bd981428-f9e9-48be-a5be-a334ed40c46e   swap                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        6128e8e7-fbc6-435f-b2ad-27d1d563e622   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        54986ED6986EB5E0                       ntfs       Expansion Drive               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/6128e8e7-fbc6-435f-b2ad-27d1d563e622 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2        /media/f0e01c40-738e-444a-9e79-a2c240dc73d9 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/FE5083AA5083686B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/b5b9a8ef-59ee-4606-b63c-95366c4bb379 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set f0e01c40-738e-444a-9e79-a2c240dc73d9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b5b9a8ef-59ee-4606-b63c-95366c4bb379
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b5b9a8ef-59ee-4606-b63c-95366c4bb379
    linux    /vmlinuz-2.6.35-22-generic root=UUID=f0e01c40-738e-444a-9e79-a2c240dc73d9 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b5b9a8ef-59ee-4606-b63c-95366c4bb379
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=f0e01c40-738e-444a-9e79-a2c240dc73d9 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b5b9a8ef-59ee-4606-b63c-95366c4bb379
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b5b9a8ef-59ee-4606-b63c-95366c4bb379
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fe5083aa5083686b
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
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=f0e01c40-738e-444a-9e79-a2c240dc73d9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=b5b9a8ef-59ee-4606-b63c-95366c4bb379 /boot           ext4    defaults        0       2
/dev/sdb5       /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=bd981428-f9e9-48be-a5be-a334ed40c46e none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  81 02 89 79 04 09 d9 b5  a2 cd 04 83 7f fc 39 81  |...y..........9.|
00000010  00 b2 08 dc 05 94 f0 1a  46 93 83 c8 0a 95 56 25  |........F.....V%|
00000020  04 32 aa 70 38 40 27 1f  ff 97 df a8 68 99 70 e8  |.2.p8@'.....h.p.|
00000030  fc 1b 82 7e 64 b5 a9 cf  1b 17 14 83 b9 e4 d4 8b  |...~d...........|
00000040  dd bf 41 ff 64 90 4d 32  e1 7d 33 c5 e2 ef 67 64  |..A.d.M2.}3...gd|
00000050  dc eb 22 c5 f2 50 c5 26  74 11 41 0a d4 8b ff d5  |.."..P.&t.A.....|
00000060  30 31 77 62 40 02 00 00  ff fb b4 04 28 80 03 38  |01wb@.......(..8|
00000070  3b d4 bd 61 a0 0a 6f ab  ca ca ac 20 01 54 a0 ef  |;..a..o.... .T..|
00000080  49 b9 ac 00 02 aa a1 69  3f 35 80 00 45 db dc c1  |I......i?5..E...|
00000090  03 42 c1 ca 66 44 ab f4  86 96 ff 93 e1 ae c8 4a  |.B..fD.........J|
000000a0  ac e8 e5 06 84 2a ca 5b  e1 02 0b f4 71 29 54 08  |.....*.[....q)T.|
000000b0  58 5e 76 38 ab 26 5a 3c  bd 3a 24 0f fe a4 77 f0  |X^v8.&Z<.:$...w.|
000000c0  30 f1 45 10 80 20 76 54  cc 5d 31 91 57 69 30 b7  |0.E.. vT.]1.Wi0.|
000000d0  dd 75 17 34 9f d7 f9 c8  f6 28 2e f4 2c bf fd 3d  |.u.4.....(..,..=|
000000e0  8d a5 a3 c3 c2 5a ad 15  3f 85 1f ff ff c6 68 fa  |.....Z..?.....h.|
000000f0  fe 8b a7 4e 1d aa b3 d1  59 5f e8 71 31 37 2b b4  |...N....Y_.q17+.|
00000100  49 da 58 ee 62 96 26 29  e1 bb b7 ff ff ff ff ff  |I.X.b.&)........|
00000110  36 30 00 80 c8 00 a3 18  5e e4 c5 82 59 1c 14 01  |60......^...Y...|
00000120  5c 19 d5 28 86 6c d5 99  4e e6 b8 08 39 68 e0 10  |\..(.l..N...9h..|
00000130  51 b3 8c 99 a0 08 4c 03  82 2c 63 18 01 03 02 e0  |Q.....L..,c.....|
00000140  5d ae 27 34 0c 5d 48 10  18 b8 0a e4 1e bf 29 a0  |].'4.]H.......).|
00000150  b0 70 5b 12 1f 48 65 f2  66 0f 33 0f 25 9e e2 34  |.p[..He.f.3.%..4|
00000160  19 4b a6 64 4c d6 c5 da  b2 fa fa a5 a4 c3 3b 91  |.K.dL.........;.|
00000170  4a 7c fb 4a 98 e3 91 48  3b 97 f6 e8 a8 13 7d fb  |J|.J...H;.....}.|
00000180  98 b1 16 bf 53 94 f2 b4  73 7f 29 ec 3f f3 70 04  |....S...s.).?.p.|
00000190  0d 1a cb ff 99 76 e6 14  9b e6 71 87 7f 28 05 b3  |.....v....q..(..|
000001a0  46 ee 4d 3c 33 d9 45 a9  68 ec b1 0e 39 2a 07 89  |F.M<3.E.h...9*..|
000001b0  30 db 02 77 7f 4f 58 00  00 01 01 00 11 0a 00 fe  |0..w.OX.........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 86 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

