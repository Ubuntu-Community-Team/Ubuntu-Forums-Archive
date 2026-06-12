---
title: "Fresh install of Ubuntu 10.10 hangs after reboot"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by CoconutHalf on 2011-03-30
Okay, be forewarned that I am extremely new to Ubuntu and Linux in general.

I'm on an HP Pavillion dv1000 laptop. I used a live CD to install Ubuntu 10.10 to an external USB hard drive. The install completed successfully, but after a reboot I am stuck on a black screen with a white cursor. Before that I see nothing but the initial HP startup screen. I am able to run the live CD without problems, and I have been running Ubuntu from a 4GB thumb drive (which I installed on using the same live CD that I used to install on my current external hard drive). I had no problems whatsoever running from the CD or thumb drive, so I can't figure out why the external hard drive would be so different. I have combed the forums and not found anything helpful. Please help - I really need to get this up and running ASAP!

---

### Post by Rubi1200 on 2011-03-30
Hi and welcome to the forums :-)

What graphics card do you have installed?

Do you get the black screen AFTER or BEFORE the GRUB menu?

---

### Post by CoconutHalf on 2011-03-30
Thanks for the welcome and the quick response! :)

Okay, as I said, I'm a noob, so hopefully I found what you need. This is what I got from lspci:

VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


I get stuck at the screen before the GRUB menu.

---

### Post by Rubi1200 on 2011-03-30
If this is happening before the GRUB menu it could indicate a couple of things; either you need to set the boot device priority in BIOS to the external drive and/or GRUB was not installed to the correct MBR.

Please post the results of the boot info script. There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by CoconutHalf on 2011-03-30
The problem shouldn't be with the boot order, as I have USB drive as the top priority.

Here are the results of the Boot Info Script (/dev/sdc is the external drive I am having issues with):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   150,159,359   150,157,312  83 Linux
/dev/sda2         150,161,406   156,301,311     6,139,906   5 Extended
/dev/sda5         150,161,408   156,301,311     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     7,372,799     7,370,752  83 Linux
/dev/sdb2           7,374,846     7,829,503       454,658   5 Extended
/dev/sdb5           7,374,848     7,829,503       454,656  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   482,256,895   482,254,848  83 Linux
/dev/sdc2         482,258,942   488,396,799     6,137,858   5 Extended
/dev/sdc5         482,258,944   488,396,799     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5b93d5b8-e3de-4003-92b6-2bf9d35a445f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ca86767e-14ea-4461-8405-0f681f5ba586   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        771bc7c9-16d1-4d4e-91f2-8daeda88eeb8   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f0822695-d583-45fa-94ca-c9e762e1e756   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        bca2648c-f6ef-4fdc-a28d-99632fd6da0a   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        5f1e1ab7-b6fd-4a1e-b01c-e7bf9b9409d6   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/bca2648c-f6ef-4fdc-a28d-99632fd6da0a ext4       (rw,nosuid,nodev,uhelper=udisks)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca86767e-14ea-4461-8405-0f681f5ba586 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/vmlinuz-2.6.35-22-generic
    .3GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 771bc7c9-16d1-4d4e-91f2-8daeda88eeb8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 771bc7c9-16d1-4d4e-91f2-8daeda88eeb8
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 771bc7c9-16d1-4d4e-91f2-8daeda88eeb8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=771bc7c9-16d1-4d4e-91f2-8daeda88eeb8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 771bc7c9-16d1-4d4e-91f2-8daeda88eeb8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=771bc7c9-16d1-4d4e-91f2-8daeda88eeb8 ro single 
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 771bc7c9-16d1-4d4e-91f2-8daeda88eeb8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 771bc7c9-16d1-4d4e-91f2-8daeda88eeb8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5b93d5b8-e3de-4003-92b6-2bf9d35a445f
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=771bc7c9-16d1-4d4e-91f2-8daeda88eeb8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=f0822695-d583-45fa-94ca-c9e762e1e756 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/core.img
    .9GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.35-22-generic
   1.0GB: boot/vmlinuz-2.6.35-22-generic
   1.4GB: initrd.img
   1.0GB: vmlinuz

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set bca2648c-f6ef-4fdc-a28d-99632fd6da0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set bca2648c-f6ef-4fdc-a28d-99632fd6da0a
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set bca2648c-f6ef-4fdc-a28d-99632fd6da0a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=bca2648c-f6ef-4fdc-a28d-99632fd6da0a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set bca2648c-f6ef-4fdc-a28d-99632fd6da0a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=bca2648c-f6ef-4fdc-a28d-99632fd6da0a ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set bca2648c-f6ef-4fdc-a28d-99632fd6da0a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set bca2648c-f6ef-4fdc-a28d-99632fd6da0a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5b93d5b8-e3de-4003-92b6-2bf9d35a445f
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=bca2648c-f6ef-4fdc-a28d-99632fd6da0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5f1e1ab7-b6fd-4a1e-b01c-e7bf9b9409d6 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 167.6GB: boot/grub/core.img
 169.8GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
 167.6GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
 167.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  07 a0 89 cf 54 aa 82 fa  76 78 58 6c 76 4f 5f bd  |....T...vxXlvO_.|
00000010  3c f4 55 a3 81 f3 ab b4  d2 a6 ea a0 a6 f1 38 2f  |<.U...........8/|
00000020  a2 a5 0f a9 17 9e 33 75  2e 88 92 5b d2 d6 b3 ec  |......3u...[....|
00000030  dc e8 cd 6f eb 85 d0 a0  3d c6 31 2d 5b bc f0 ee  |...o....=.1-[...|
00000040  87 e9 60 80 4d 4f 1a bd  79 da dc 83 fa 13 90 4d  |..`.MO..y......M|
00000050  ce a7 94 4a 08 6d 24 4c  54 10 6e 6d e9 7d ab a5  |...J.m$LT.nm.}..|
00000060  cf 8a 43 4c 90 db 20 99  86 cc 5e c4 7b e4 2c 8b  |..CL.. ...^.{.,.|
00000070  f7 59 a5 fb 01 15 96 a2  7a 11 02 1a fa 0e 40 a9  |.Y......z.....@.|
00000080  c2 c5 29 eb 7b e5 b6 3e  5c f1 b3 ad dd 9a 6b 0d  |..).{..>\.....k.|
00000090  ad e0 c0 57 ec 4d 92 0f  2d d9 52 60 85 24 ac 85  |...W.M..-.R`.$..|
000000a0  94 5a a3 06 08 bb 32 97  b8 9a 88 2d f2 89 25 ec  |.Z....2....-..%.|
000000b0  36 84 44 16 18 ff a1 a4  58 c7 62 7c 36 7e 72 c4  |6.D.....X.b|6~r.|
000000c0  2f dd b8 40 2c b0 11 3c  68 39 09 83 8c 7e a1 5c  |/..@,..<h9...~.\|
000000d0  c0 d2 e0 aa 4c 06 af 91  e4 f8 59 33 09 0c 34 ee  |....L.....Y3..4.|
000000e0  6d eb 65 31 eb 22 47 e7  b7 a5 10 ef 64 5b 21 5c  |m.e1."G.....d[!\|
000000f0  e0 80 c8 4f d0 b8 5a eb  c5 43 a8 57 f3 a8 b1 bf  |...O..Z..C.W....|
00000100  64 42 20 2f d1 7e ef d9  60 96 bb 98 24 49 5f aa  |dB /.~..`...$I_.|
00000110  95 78 6a c5 ae 73 08 f3  30 0c 29 61 61 be 57 8a  |.xj..s..0.)aa.W.|
00000120  d3 10 e4 77 1a 2d 14 c8  6a a3 fb 50 63 eb 55 07  |...w.-..j..Pc.U.|
00000130  60 f3 ae a8 e2 cf e9 52  7d ad 21 d5 cf 65 a9 1e  |`......R}.!..e..|
00000140  85 48 b2 1f 34 93 7a c1  c0 68 9d 12 0e ec cb 56  |.H..4.z..h.....V|
00000150  24 21 ac 13 38 97 73 04  57 80 94 0f e1 fe 3a 43  |$!..8.s.W.....:C|
00000160  b8 07 24 a9 86 11 33 86  05 7c 36 82 a3 62 b3 51  |..$...3..|6..b.Q|
00000170  36 dc cd 57 30 1a 02 fe  ff c8 f8 bf 85 9a 4b c5  |6..W0.........K.|
00000180  00 96 b8 6a 59 56 52 f8  34 65 03 0f 59 e4 06 93  |...jYVR.4e..Y...|
00000190  e1 55 c0 77 e7 58 c2 57  18 09 2f 1a b2 3e 91 fc  |.U.w.X.W../..>..|
000001a0  18 71 ff 32 63 b4 7d db  5e c4 58 d2 90 8f 11 fc  |.q.2c.}.^.X.....|
000001b0  41 3f 8d 44 3f fb c5 a3  9c 51 73 fd 3b 35 00 fe  |A?.D?....Qs.;5..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  0a 53 13 57 20 59 6b f8  6a ba 71 35 d6 2e 59 ba  |.S.W Yk.j.q5..Y.|
00000010  60 d7 e9 c5 19 f6 46 a9  fb c2 c4 67 72 35 46 d5  |`.....F....gr5F.|
00000020  0b f1 4a 97 9d 1a e3 2a  af 4c 1d ca e5 67 fa 58  |..J....*.L...g.X|
00000030  85 a4 ed 7b ed 0e f5 8d  3b 66 f0 63 11 62 93 df  |...{....;f.c.b..|
00000040  de c3 87 bc f1 4e c9 92  95 e0 36 4e 55 9c 1b 5f  |.....N....6NU.._|
00000050  e3 15 c7 02 f4 96 e7 6a  5d 5a 5e 1b 3d 70 16 90  |.......j]Z^.=p..|
00000060  be af 73 2c 77 f7 b7 76  c9 c9 71 6d 9b 0b 25 3d  |..s,w..v..qm..%=|
00000070  af bb 76 f5 c5 25 12 5b  bf 26 d5 ba e7 a6 19 6a  |..v..%.[.&.....j|
00000080  56 2a e6 b7 70 26 f8 8e  74 1a 26 9d 19 9a a5 d0  |V*..p&..t.&.....|
00000090  ee 4a 89 22 ba 86 5b 05  f2 e4 72 93 d4 89 67 ef  |.J."..[...r...g.|
000000a0  5c 18 22 4b 68 77 6f dc  4e 15 dd 4d c6 14 b3 2d  |\."Khwo.N..M...-|
000000b0  52 8c 18 9a 65 85 69 bb  0d 0b 0b 67 a2 df 0b d3  |R...e.i....g....|
000000c0  ae 07 03 35 66 6f 41 be  6e df 6b 8a 40 90 e4 23  |...5foA.n.k.@..#|
000000d0  e0 d7 16 32 f5 21 9c cf  1c 71 47 f9 24 01 95 48  |...2.!...qG.$..H|
000000e0  37 2c 2d f1 b5 5a fb 7a  5c ee f0 f2 ec 79 5b 99  |7,-..Z.z\....y[.|
000000f0  75 ac ed cd f6 5e 76 aa  31 75 2e 0a 7a 9e c4 12  |u....^v.1u..z...|
00000100  a7 ea 79 1a e2 ee e0 11  a8 93 91 4a e7 ea 22 7f  |..y........J..".|
00000110  db d5 17 06 4b 0c fe 62  ae db b8 9b 56 b5 49 eb  |....K..b....V.I.|
00000120  28 3c bb ed bd 51 75 e6  44 ca be 1a 26 4c 18 10  |(<...Qu.D...&L..|
00000130  73 93 c3 07 b1 1d ae c3  5f da bb 60 4a d7 c3 de  |s......._..`J...|
00000140  d6 f8 5f 12 ee 16 72 e4  f9 b5 2b a5 ad 57 8e de  |.._...r...+..W..|
00000150  71 25 e9 89 c4 ee 1e e7  a9 0b 1e 3c 70 a0 60 de  |q%.........<p.`.|
00000160  98 67 0e 14 08 cb 1e 42  16 7b 74 74 d8 6c 39 af  |.g.....B.{tt.l9.|
00000170  fa 5b 65 1b bd c0 96 bd  10 ec 67 43 2f 7a d1 7e  |.[e.......gC/z.~|
00000180  68 b5 d2 3b 6f 15 23 57  56 a8 d7 85 6e b4 03 63  |h..;o.#WV...n..c|
00000190  18 ed 2c 15 48 91 d5 17  fa d5 f1 46 47 0b 60 77  |..,.H......FG.`w|
000001a0  5f 5a 31 34 e6 63 ca 9b  53 8f f0 d3 b0 4e ed 4c  |_Z14.c..S....N.L|
000001b0  53 a5 4d 8e 02 6b d2 e6  37 42 42 17 30 a2 00 10  |S.M..k..7BB.0...|
000001c0  46 cb 82 5c 75 e7 02 00  00 00 00 f0 06 00 00 00  |F..\u...........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  fb 96 f6 cf bd 76 35 ba  4e 2f 5c d5 9f ce 00 02  |.....v5.N/\.....|
00000010  76 a8 2f eb d4 76 fd 75  08 87 22 08 b5 2e 72 7e  |v./..v.u.."...r~|
00000020  0a 63 d8 b7 77 5e 6d 3c  93 8b bc 24 60 53 0a 77  |.c..w^m<...$`S.w|
00000030  40 b3 ac 81 a5 48 bd c5  c6 34 cb ac e0 1c 3d e2  |@....H...4....=.|
00000040  0e 75 6d a0 9a 00 fb b6  84 67 90 f8 be 50 ba ef  |.um......g...P..|
00000050  d3 7b 33 4f b3 1e ec 8e  14 5a 6d 5a a6 94 68 26  |.{3O.....ZmZ..h&|
00000060  12 7e 33 0d 6f 80 57 b2  07 6c ce b8 2c 16 44 89  |.~3.o.W..l..,.D.|
00000070  e3 d3 b4 d9 a2 bd 3e 9e  11 b2 08 bf 39 2e f7 8f  |......>.....9...|
00000080  a2 6e c7 23 b4 fd 8e 0a  7e 58 7c 0a 8f 0e ef 91  |.n.#....~X|.....|
00000090  f4 e0 fe 78 a8 7c 14 d0  72 74 cf 27 9b b6 09 3a  |...x.|..rt.'...:|
000000a0  61 1d af df cf 07 66 59  72 56 85 14 65 42 a6 89  |a.....fYrV..eB..|
000000b0  ea 2d b5 0e a7 66 6d 78  c4 42 bf c2 94 23 cb 94  |.-...fmx.B...#..|
000000c0  65 52 ee df c7 56 90 51  9b a7 38 19 6c 1c d1 17  |eR...V.Q..8.l...|
000000d0  88 b6 ec df ba ad 45 4e  7e 56 53 3c ad 04 3d 39  |......EN~VS<..=9|
000000e0  0e eb 6b 39 b4 37 d5 0d  1a b5 dd b1 6a ea 87 bb  |..k9.7......j...|
000000f0  99 82 e3 b5 c5 e3 44 fb  73 94 2e b4 1b 10 46 88  |......D.s.....F.|
00000100  cb 6f ce 87 42 06 db f9  8a 43 3b fb bb 4e 3c 3a  |.o..B....C;..N<:|
00000110  77 d3 28 29 08 7e 10 99  bb db f0 83 e3 d4 ae a5  |w.().~..........|
00000120  21 d6 a1 0a 7e 47 91 e3  c0 11 2e fd 4a 38 5e 3f  |!...~G......J8^?|
00000130  9a ec 4c 94 09 0f 20 20  59 70 54 f6 39 3a 01 98  |..L...  YpT.9:..|
00000140  de e2 06 02 d8 a6 1d 7a  e0 7e d6 6a 98 f7 49 df  |.......z.~.j..I.|
00000150  b4 e0 51 cb b2 e8 f0 78  f8 90 61 3c 76 6c 71 ec  |..Q....x..a<vlq.|
00000160  45 ff 06 cc 32 56 45 63  8a 15 6e 8f 04 c0 82 f7  |E...2VEc..n.....|
00000170  10 17 2b 9c b3 a0 dc 48  ab 94 eb ac bd e5 2d 5e  |..+....H......-^|
00000180  21 ed 33 39 16 6d d7 ff  d7 db cd ae d6 10 ec 6b  |!.39.m.........k|
00000190  7f 9c f9 0b d1 aa 7f bd  cc f2 97 cb da bc 80 49  |...............I|
000001a0  7b 25 e3 18 8f 5e 16 7c  d1 19 b7 2a 14 aa 43 5a  |{%...^.|...*..CZ|
000001b0  87 d5 4e 22 d2 2f 2f 3d  02 d6 73 f5 32 30 00 fe  |..N".//=..s.20..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rubi1200 on 2011-03-30
This is probably the problem:


>  => No boot loader is installed in the MBR of /dev/sdc

What happened when you installed and it came time to install the bootloader?

Theoretically, reinstalling GRUB to the MBR of sdc should fix it:
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

---

### Post by CoconutHalf on 2011-03-30
I was able to fix the GRUB install using the directions in the link you provided. The first two methods didn't work for me, but luckily the third one (using chroot) worked perfectly. Thank you so much for you help! :) There's no way I could have figured this out on my own.

---

### Post by Rubi1200 on 2011-03-30
No problem, you are more than welcome :-)

I am pleased you got this sorted out. Yes, sometimes the chroot method is needed if the other 2 don't work.

Enjoy!

---

