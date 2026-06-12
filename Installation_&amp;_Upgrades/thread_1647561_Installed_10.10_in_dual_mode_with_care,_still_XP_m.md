---
title: "Installed 10.10 in dual mode with care, still XP missing"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by amjain on 2010-12-17
I have a lenevo laptop (with XP originally)
I installed wubi first, used for couple of days. Later I installed 10.10 from the Live CD and chose dual option. 
But now in the boot loader menu there is no XP option. I have been googling for many hours now without hitting any solution.
I believe I have not erased my XP install and/or data. All I want is to add the XP to the boot loader options. 
Here is the result of fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3918    31464688+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3918       19458   124825297+   f  W95 Ext'd (LBA)
/dev/sda5            3918        9140    41950408+   7  HPFS/NTFS
/dev/sda6            9140       12550    27389848+   7  HPFS/NTFS
/dev/sda7           12550       16479    31555408+   7  HPFS/NTFS
/dev/sda8           16479       18910    19530752   83  Linux
/dev/sda9           18910       19458     4397056   82  Linux swap / Solaris

Please help. 
regards,
Amit

---

### Post by karthick87 on 2010-12-17
Welcome to ubuntu forums :)

Have you tried,
```
sudo update-grub
```If that din help you,post the results of bootinfoscript from my signature.

---

### Post by wilee-nilee on 2010-12-17
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by Rubi1200 on 2010-12-17
Hi and welcome to the forums Amit :)

Go to Applications > Accessories > Terminal and run this command:

```
sudo update-grub
```

Does it show Windows XP?

If yes, restart and all should be good.

If not, run the boot info script linked at the bottom of my post and get the results back here please.

Thanks.

---

### Post by amjain on 2010-12-17
Thanks to all for responding so quick. 
I am attaching the RESULTS.txt file 

Please let me know if I should paste the content. Its 476 lines. 

regards,
Amit

---

### Post by sikander3786 on 2010-12-17
*karthick87 *also posted the Results.txt below.

---

### Post by karthick87 on 2010-12-17
@amjain

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda6/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    62,929,439    62,929,377   7 HPFS/NTFS
/dev/sda2          62,929,501   312,580,095   249,650,595   f W95 Ext d (LBA)
/dev/sda5          62,929,503   146,830,319    83,900,817   7 HPFS/NTFS
/dev/sda6         146,830,383   201,610,079    54,779,697   7 HPFS/NTFS
/dev/sda7         201,610,143   264,720,959    63,110,817   7 HPFS/NTFS
/dev/sda8         264,722,432   303,783,935    39,061,504  83 Linux
/dev/sda9         303,785,984   312,580,095     8,794,112  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       c6c78b1d-f8b7-4ec3-b11a-c228ff6030aa   ext4                                     
/dev/sda1        1848B47748B4556A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        F02887A928876D82                       ntfs       CCPU                          
/dev/sda6        01CB77B63B7297B0                       ntfs       Amit                          
/dev/sda7        01CB77B63D994840                       ntfs       DontBackup                    
/dev/sda8        8428c335-600f-4766-a3e5-6b2f38a48947   ext4                                     
/dev/sda9        8c0ad00a-b7d6-44df-bce5-bde2c2f2dfd4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/1848B47748B4556A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/DontBackup        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=C:\wubildr.mbr 
[operating systems] 
C:\wubildr.mbr="Ubuntu" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

======================== sda6/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 01cb77b63b7297b0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 01cb77b63b7297b0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 01cb77b63b7297b0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 01cb77b63b7297b0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1848b47748b4556a
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

============================= sda6/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda6    /host    fuseblk    defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096    0    0
/dev/sda1    /media/c    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda5    /media/d    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda6    /media/f    fuseblk    defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096    0    0
/dev/sda7    /media/g    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda8    /media/h    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda9    /media/sda9    ntfs    defaults,nls=utf8,umask=0222    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0



================= sda6/Wubi: Location of files loaded by Grub: =================


   2.3GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.35-22-generic
   1.4GB: boot/initrd.img-2.6.35-23-generic
   1.3GB: boot/vmlinuz-2.6.35-22-generic
    .2GB: boot/vmlinuz-2.6.35-23-generic
   1.4GB: initrd.img
   1.4GB: initrd.img.old
    .2GB: vmlinuz
   1.3GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 8428c335-600f-4766-a3e5-6b2f38a48947
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 8428c335-600f-4766-a3e5-6b2f38a48947
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 8428c335-600f-4766-a3e5-6b2f38a48947
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8428c335-600f-4766-a3e5-6b2f38a48947 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 8428c335-600f-4766-a3e5-6b2f38a48947
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8428c335-600f-4766-a3e5-6b2f38a48947 ro single 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 8428c335-600f-4766-a3e5-6b2f38a48947
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 8428c335-600f-4766-a3e5-6b2f38a48947
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1848b47748b4556a
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
/dev/sda9       none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 148.6GB: boot/grub/core.img
 152.8GB: boot/grub/grub.cfg
 136.5GB: boot/initrd.img-2.6.35-22-generic
 148.6GB: boot/vmlinuz-2.6.35-22-generic
 136.5GB: initrd.img
 148.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  99 2f 24 70 cb 2e 20 b8  f0 1b de 33 5a 74 c3 0a  |./$p.. ....3Zt..|
00000010  e5 3c 53 1b 77 b9 61 01  47 c0 dc 16 1f 2e 58 ef  |.<S.w.a.G.....X.|
00000020  59 3d 7a ae 39 a0 5b 4a  88 40 da cc f0 c1 e6 5e  |Y=z.9.[J.@.....^|
00000030  ab 6c 9f 7b 0f bb 5d 21  12 4a a2 91 01 b5 b1 e4  |.l.{..]!.J......|
00000040  95 61 f4 a0 5c 91 76 72  b8 af e9 c1 d9 eb ba 78  |.a..\.vr.......x|
00000050  0d a4 d3 16 90 6f b1 5c  55 89 0f 46 fb ae 37 59  |.....o.\U..F..7Y|
00000060  b1 e2 18 3c cb e1 58 1b  56 f8 f6 fa 6e c7 a7 0f  |...<..X.V...n...|
00000070  12 87 a1 6d 72 63 58 64  0d da 74 9b 1e b6 4b 1e  |...mrcXd..t...K.|
00000080  27 56 d6 6c 78 e0 7f 83  83 b1 a5 7d 87 89 6d 32  |'V.lx......}..m2|
00000090  85 dc 06 cb 18 4c 05 1e  c1 2d 45 3a 5b c2 3f b6  |.....L...-E:[.?.|
000000a0  23 72 6f b4 81 f1 c0 6e  a9 c3 4a 4c 2a ac 49 f4  |#ro....n..JL*.I.|
000000b0  21 3e d8 43 c8 43 63 1f  a4 e6 29 3c 06 dc 66 4a  |!>.C.Cc...)<..fJ|
000000c0  71 0f 17 ec 42 15 a9 82  3d af 22 98 77 29 1c aa  |q...B...=.".w)..|
000000d0  9e 35 8c f0 54 05 38 c0  48 40 1d 20 32 7a 75 49  |.5..T.8.H@. 2zuI|
000000e0  d9 33 78 f5 6a a5 8f 31  69 f0 1b 08 91 ba 43 18  |.3x.j..1i.....C.|
000000f0  a3 e8 9e 4c 0d 34 2d 5b  47 db e4 47 82 19 ae 06  |...L.4-[G..G....|
00000100  80 36 9d 9c 8b 9d 97 ab  5b df 23 8f 5d b4 e7 a7  |.6......[.#.]...|
00000110  2b e4 32 03 68 b7 25 3e  6e 55 0f 5f 47 f1 d7 aa  |+.2.h.%>nU._G...|
00000120  fc da f1 f0 f2 80 d9 e8  af 90 8d 65 63 fe 23 3a  |...........ec.#:|
00000130  34 56 ac b0 84 eb 23 f5  2b 1f 93 c7 d4 0d 99 65  |4V....#.+......e|
00000140  3c d3 2b 88 43 f9 ee 13  2f 76 d7 92 1e 6d eb 8b  |<.+.C.../v...m..|
00000150  ad 40 b3 94 f0 1b 22 c7  fc cf a1 e1 6a 54 95 e3  |.@....".....jT..|
00000160  41 28 bc b3 86 9c 4f e2  4b 43 41 bd f5 94 e1 39  |A(....O.KCA....9|
00000170  fc d2 30 36 73 e2 54 41  21 f6 21 4f a6 bc d7 22  |..06s.TA!.!O..."|
00000180  94 4b 55 ee 6a 97 26 5c  10 c7 cc c5 f6 1f 52 dd  |.KU.j.&\......R.|
00000190  e7 08 0c 51 42 d0 36 c0  fb 34 3e 9c 23 3e d2 44  |...QB.6..4>.#>.D|
000001a0  ec f8 fa c3 b5 6a 93 a8  c6 a9 f0 be 25 35 9e 6a  |.....j......%5.j|
000001b0  1f 69 f1 c6 11 2c 6a 6a  d5 e0 6c e8 f7 52 00 ef  |.i...,jj..l..R..|
000001c0  ff ff 07 ef ff ff 02 00  00 00 91 39 00 05 00 fe  |...........9....|
000001d0  ff ff 05 fe ff ff 93 39  00 05 70 df 43 03 00 00  |.......9..p.C...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by sikander3786 on 2010-12-17
XP is still there and Grub is able to see it as you see in your grub.cfg,

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 1848b47748b4556a
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


Wubi boot files are still there on both sda1 and sda6 and you need to remove them. Wilee-nilee or Rubi1200 might have some better suggestion on that. I just have the one to *fixmbr* for XP ;-)

Another problem might be this lying on sda6,

>     Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.


Your Grub menu is not that populated but due to some resolution problems, the box might be reduced in size (??). Did you scroll down using the arrow keys on your Grub menu to find XP?

---

### Post by amjain on 2010-12-17
Thanks Sikander, 
Yes I did scroll down on the grub file in vi, if thats what you mean. 
So what should I try now - Changing the 1 line in grub.cfg file manually 

from 
```
menuentry "Ubuntu (on /dev/sda1)" {
```to 
```
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
```
Will I need to run some other command (like update grub) after that.

regards,
Amit

---

### Post by sikander3786 on 2010-12-17
_Donot_ edit  your grub.cfg.

Do you see the Grub menu when you boot your PC right after the Bios screen? Did you scroll down in that menu to find XP?

As I had a better look at your Results.txt, I felt I was not reading that correctly previously.

You'll need to fixmbr from a Windows Disc or install Lilo.

Wait for Rubi1200 or wilee-nilee to reply. I was not supposed to be here :-)

---

### Post by Rubi1200 on 2010-12-17
Here is my take on the situation.

You have Wubi files in the XP boot sector that need to be removed:
sda1:
```
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/wubildr.mbr /wubildr[/COLOR]
```

The menuentry for XP that GRUB is picking up on is correct and I see no reason to change it.

I advise you to restore the Windows bootloader, delete the Wubi install from within Windows using Add/Remove Programs, and finally reinstall GRUB using a LiveCD.

---

### Post by amjain on 2010-12-18
OK the problem is solved. I did not had a XP cd, so all I did was rebooted and choose the ubuntu (which was installed from wubi). There it presented with next boot menu which was exactly same as before I installed the ubuntu independently. So I could login to Windows.  In there, used a utility call MbrFix which does not require XP cd to fix the mbr. [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)  There after used the XP bootcfg command to correct the Boot.ini.  At this point, ubuntu was gone and XP was as it was originally from boot loader perspective.   Next step was to run the live CD and use the steps as mentioned in [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).    Thanks for all help.

---

### Post by Rubi1200 on 2010-12-18
Excellent! I am really pleased you got things sorted out :)

You can mark this thread Solved using the Thread Tools near the top of the page.

By the way, nice way to do it booting into the old Wubi install ;)

---

### Post by amjain on 2010-12-18
I dont know how to mark this thread as solved. Please suggest.

---

### Post by Rubi1200 on 2010-12-18
When you are in the thread, you will see a Thread Tools menu near the top right hand side of the page. One of the menu options is mark Solved.

---

