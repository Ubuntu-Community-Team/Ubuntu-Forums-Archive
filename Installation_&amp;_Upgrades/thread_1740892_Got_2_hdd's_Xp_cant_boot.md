---
title: "Got 2 hdd's Xp cant boot"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by lightdt on 2011-04-27
l got 2 hdd's in a Toshiba Qosmio g30 laptop.

Its my first time installing linex and i think I picked the hdd no.2 to install Ubuntu (am not sure because Ubuntu CD software gave me a chose between 2 identical drives similar names and no) 

after restart and ejecting the Ubuntu CD. Nothing booted up, no windows Xp or Ubuntu beside some command prompt with listing but its not booting up. only thing that worked there is memo test thing.

So I try the Ubuntu Cd again but this time install on the opposite hdd then the one before which now works. 

Now I have a working Ubuntu but cant find the option to load/boot Windows XP.

I need help as so far i dont know how to get rid off the non working Ubuntu on hdd no.2 and how to recover my windows XP. am afraid if I try to fix it anymore will cause it more harm. 

I really wanted duel boots and still do, please help.

---

### Post by oldfred on 2011-04-27
Welcome to the forum.

From liveCD post this, so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by lightdt on 2011-04-28
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   134,817,643   134,817,581   7 HPFS/NTFS
/dev/sdb2         134,817,790   234,440,703    99,622,914   5 Extended
/dev/sdb5         134,817,792   230,275,071    95,457,280  83 Linux
/dev/sdb6         230,277,120   234,440,703     4,163,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9f1a2d98-9c22-427a-83a8-0ee48a8337a5   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7504ccbd-b274-4fa8-b99b-da393aa49aec   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        807C847D7C846FA8                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        22d2d6c6-887d-49e4-a67d-b776eeff7985   ext4                                     
/dev/sdb6        5d78a296-0875-480b-a2a8-0173b759130e   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 9f1a2d98-9c22-427a-83a8-0ee48a8337a5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 9f1a2d98-9c22-427a-83a8-0ee48a8337a5
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9f1a2d98-9c22-427a-83a8-0ee48a8337a5
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=9f1a2d98-9c22-427a-83a8-0ee48a8337a5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9f1a2d98-9c22-427a-83a8-0ee48a8337a5
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=9f1a2d98-9c22-427a-83a8-0ee48a8337a5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9f1a2d98-9c22-427a-83a8-0ee48a8337a5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9f1a2d98-9c22-427a-83a8-0ee48a8337a5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 22d2d6c6-887d-49e4-a67d-b776eeff7985
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=22d2d6c6-887d-49e4-a67d-b776eeff7985 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 22d2d6c6-887d-49e4-a67d-b776eeff7985
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=22d2d6c6-887d-49e4-a67d-b776eeff7985 ro single
    initrd /boot/initrd.img-2.6.35-28-generic-pae
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
UUID=7504ccbd-b274-4fa8-b99b-da393aa49aec none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/core.img
  60.2GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-28-generic-pae
 111.8GB: boot/vmlinuz-2.6.35-28-generic-pae
    .9GB: initrd.img
 111.8GB: vmlinuz

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 22d2d6c6-887d-49e4-a67d-b776eeff7985
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 22d2d6c6-887d-49e4-a67d-b776eeff7985
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 22d2d6c6-887d-49e4-a67d-b776eeff7985
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=22d2d6c6-887d-49e4-a67d-b776eeff7985 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 22d2d6c6-887d-49e4-a67d-b776eeff7985
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=22d2d6c6-887d-49e4-a67d-b776eeff7985 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 22d2d6c6-887d-49e4-a67d-b776eeff7985
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 22d2d6c6-887d-49e4-a67d-b776eeff7985
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9f1a2d98-9c22-427a-83a8-0ee48a8337a5
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=9f1a2d98-9c22-427a-83a8-0ee48a8337a5 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9f1a2d98-9c22-427a-83a8-0ee48a8337a5
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=9f1a2d98-9c22-427a-83a8-0ee48a8337a5 ro single
    initrd /boot/initrd.img-2.6.35-28-generic-pae
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=22d2d6c6-887d-49e4-a67d-b776eeff7985 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5d78a296-0875-480b-a2a8-0173b759130e none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


  75.6GB: boot/grub/core.img
  95.1GB: boot/grub/grub.cfg
  91.3GB: boot/initrd.img-2.6.35-28-generic-pae
  75.6GB: boot/vmlinuz-2.6.35-28-generic-pae
  91.3GB: initrd.img
  75.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  41 a5 cc 7c 9f bb 7a 22  1d 71 48 68 bb c7 36 4e  |A..|..z".qHh..6N|
00000010  79 bd 44 d4 57 53 72 fa  55 89 c0 c0 73 5f 2e 26  |y.D.WSr.U...s_.&|
00000020  b1 d5 bc 2c 0f eb 6a d2  8d a1 38 18 2b f7 26 fe  |...,..j...8.+.&.|
00000030  e9 ed 34 84 c7 83 62 aa  c5 b9 b0 70 e3 8f 1e d6  |..4...b....p....|
00000040  21 05 ac dc 7f 1b 5a 82  fd d1 28 c8 9b 27 16 ae  |!.....Z...(..'..|
00000050  59 1d 24 34 37 b3 52 5a  35 e9 a0 20 53 bf 0e 86  |Y.$47.RZ5.. S...|
00000060  91 35 9c 8c ef 4b 4a 32  6d 01 18 78 0b 57 06 5e  |.5...KJ2m..x.W.^|
00000070  c9 4d 14 e4 a7 e3 42 0a  a5 19 90 d0 c3 ef fe 36  |.M....B........6|
00000080  01 65 8c 3c 5f 7b 3a e2  dd 31 08 28 7b 87 f6 0e  |.e.<_{:..1.({...|
00000090  39 7d 04 94 17 13 32 ba  15 49 80 80 33 1f ee e6  |9}....2..I..3...|
000000a0  71 95 7c ec cf ab 2a 92  4d 61 f8 d8 eb b7 e6 be  |q.|...*.Ma......|
000000b0  a9 ad f4 44 87 43 22 6a  85 79 70 30 a3 4f de 96  |...D.C"j.yp0.O..|
000000c0  e1 c5 6c 9c 3f db 1a 42  bd 91 e8 88 5b e7 d6 6e  |..l.?..B....[..n|
000000d0  19 dd e4 f4 f7 73 12 1a  f5 a9 60 e0 13 7f ce 46  |.....s....`....F|
000000e0  51 f5 5c 4c af 0b 0a f2  2d c1 d8 38 cb 17 c6 1e  |Q.\L....-..8....|
000000f0  89 0d d4 a4 67 a3 02 ca  65 d9 50 90 83 af be f6  |....g...e.P.....|
00000100  c1 25 4c fc 1f 3b fa a2  9d f1 c8 e8 3b 47 b6 ce  |.%L..;......;G..|
00000110  f9 3d c4 54 d7 d3 f2 7a  d5 09 40 40 f3 df ae a6  |.=.T...z..@@....|
00000120  31 55 3c ac 8f 6b ea 52  0d 21 b8 98 ab 77 a6 7e  |1U<..k.R.!...w.~|
00000130  69 6d b4 04 47 03 e2 2a  45 39 30 f0 63 0f 9e 56  |im..G..*E90.c..V|
00000140  a1 85 2c 5c ff 9b da 02  7d 51 a8 48 1b a7 96 2e  |..,\....}Q.H....|
00000150  d9 9d a4 b4 b7 33 d2 da  b5 69 20 a0 d3 3f 8e 06  |.....3...i ..?..|
00000160  11 b5 1c 0c 6f cb ca b2  ed 81 98 f8 8b d7 86 de  |....o...........|
00000170  49 cd 94 64 27 63 c2 8a  25 99 10 50 43 6f 7e b6  |I..d'c..%..PCo~.|
00000180  81 e5 0c bc df fb ba 62  5d b1 88 a8 fb 07 76 8e  |.......b].....v.|
00000190  b9 fd 84 14 97 93 b2 3a  95 c9 00 00 b3 9f 6e 66  |.......:......nf|
000001a0  f1 15 fc 6c 4f 2b aa 12  cd e1 78 58 6b 37 66 3e  |...lO+....xXk7f>|
000001b0  29 2d 74 c4 07 c3 a2 ea  05 f9 f0 b0 23 cf 00 fe  |)-t.........#...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  b9 fd 84 14 97 93 b2 3a  95 c9 00 00 b3 9f 6e 66  |.......:......nf|
00000010  f1 15 fc 6c 4f 2b aa 12  cd e1 78 58 6b 37 66 3e  |...lO+....xXk7f>|
00000020  29 2d 74 c4 07 c3 a2 ea  05 f9 f0 b0 23 cf 5e 16  |)-t.........#.^.|
00000030  61 45 ec 1c bf 5b 9a c2  3d 11 68 08 db 67 56 ee  |aE...[..=.h..gV.|
00000040  99 5d 64 74 77 f3 92 9a  75 29 e0 60 93 ff 4e c6  |.]dtw...u).`..N.|
00000050  d1 75 dc cc 2f 8b 8a 72  ad 41 58 b8 4b 97 46 9e  |.u../..r.AX.K.F.|
00000060  09 8d 54 24 e7 23 82 4a  e5 59 d0 10 03 2f 3e 76  |..T$.#.J.Y.../>v|
00000070  41 a5 cc 7c 9f bb 7a 22  1d 71 48 68 bb c7 36 4e  |A..|..z".qHh..6N|
00000080  79 bd 44 d4 57 53 72 fa  55 89 c0 c0 73 5f 2e 26  |y.D.WSr.U...s_.&|
00000090  b1 d5 bc 2c 0f eb 6a d2  8d a1 38 18 2b f7 26 fe  |...,..j...8.+.&.|
000000a0  e9 ed 34 84 c7 83 62 aa  c5 b9 b0 70 e3 8f 1e d6  |..4...b....p....|
000000b0  21 05 ac dc 7f 1b 5a 82  fd d1 28 c8 9b 27 16 ae  |!.....Z...(..'..|
000000c0  59 1d 24 34 37 b3 52 5a  35 e9 a0 20 53 bf 0e 86  |Y.$47.RZ5.. S...|
000000d0  91 35 9c 8c ef 4b 4a 32  6d 01 18 78 0b 57 06 5e  |.5...KJ2m..x.W.^|
000000e0  c9 4d 14 e4 a7 e3 42 0a  a5 19 90 d0 c3 ef fe 36  |.M....B........6|
000000f0  01 65 8c 3c 5f 7b 3a e2  dd 31 08 28 7b 87 f6 0e  |.e.<_{:..1.({...|
00000100  39 7d 04 94 17 13 32 ba  15 49 80 80 33 1f ee e6  |9}....2..I..3...|
00000110  71 95 7c ec cf ab 2a 92  4d 61 f8 d8 eb b7 e6 be  |q.|...*.Ma......|
00000120  a9 ad f4 44 87 43 22 6a  85 79 70 30 a3 4f de 96  |...D.C"j.yp0.O..|
00000130  e1 c5 6c 9c 3f db 1a 42  bd 91 e8 88 5b e7 d6 6e  |..l.?..B....[..n|
00000140  19 dd e4 f4 f7 73 12 1a  f5 a9 60 e0 13 7f ce 46  |.....s....`....F|
00000150  51 f5 5c 4c af 0b 0a f2  2d c1 d8 38 cb 17 c6 1e  |Q.\L....-..8....|
00000160  89 0d d4 a4 67 a3 02 ca  65 d9 50 90 83 af be f6  |....g...e.P.....|
00000170  c1 25 4c fc 1f 3b fa a2  9d f1 c8 e8 3b 47 b6 ce  |.%L..;......;G..|
00000180  f9 3d c4 54 d7 d3 f2 7a  d5 09 40 40 f3 df ae a6  |.=.T...z..@@....|
00000190  31 55 3c ac 8f 6b ea 52  0d 21 b8 98 ab 77 a6 7e  |1U<..k.R.!...w.~|
000001a0  69 6d b4 04 47 03 e2 2a  45 39 30 f0 63 0f 9e 56  |im..G..*E90.c..V|
000001b0  a1 85 2c 5c ff 9b da 02  7d 51 a8 48 1b a7 00 fe  |..,\....}Q.H....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 b0 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff 80 92  b0 05 82 8d 3f 00 00 00  |............?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by oldfred on 2011-04-28
It looks like you installed Ubuntu twice. Once to the entire drive sda and to partition sdb5 with a NTFS partition sdb1. But the sdb1 partition has no boot files and looks just like a data partition.

The windows boot loader is in the MBR of sdb but without any boot files and sdb1, it will not boot. Using Nautilus file browers do you see a windows install in sdb1 or just what was some of your data.

A XP bootable partition should look like this in boot script:

```
sda1: ______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```

---

### Post by lightdt on 2011-04-28
yea I installed twice, had no choice.

Using the Nautilus I cant find any folder or file called sdb1, how do i get there? I dont recognize any files on the first main hdd but I have found my documents (vids,music,stuff) on the the hdd2.

is it possible that XP partition section got written over by ubuntu install on hdd1.

If so, I still have the Toshiba reformat CD if all hope fail.

I don't know much about Partitions at all.


any suggestions is really appreciated

---

### Post by oldfred on 2011-04-28
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If your important data was in the sdb NTFS partition you are lucky. But if you had any vital data you may be able to recover some of it. Ubuntu is not large and has overwritten only part of sda. testdisk's photorec may be able to recover some data, but it is a long process and the files do not have names, just extensions as all data linking filenames to locations on drives is gone.

Your vendor recovery CD/DVD may work. IfSo just a cd it may want to find the recovery partition on your hard drive which is also gone.

Some windows backup tool suggestions. You should always have good backups before making system changes.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

If installing Ubuntu to a second drive, this is a good source. Not as complex as it may look as Herman has lots of detail and explains many things.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by lightdt on 2011-04-28
Thanks for all your help the links are comprehensive.

I should have read more about it I guess. 

I'll start reformatting tomorrow morning and then reattempt to install Ubuntu on second hdd


/peace

---

