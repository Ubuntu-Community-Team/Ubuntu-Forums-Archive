---
title: "Merge 2 x Ubuntu Partitions"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by TheMadMan on 2010-12-04
Hi Guys,

Ok, I have a laptop with 2 x different versions of Ubuntu installed as follows:

Ubuntu 10.10 on a partition; and
Ubuntu ultimate edition gamers (based on ubuntu 10.10 I believe).

I've only recently installed the gamers edition as a dual boot to see what it looks like. Now I've had a play around with it I've realised that I don;t really like it.  

What's the quickest/easiest way of reverting back to my original ubuntu 10.10 as a single boot?  I don't want to re-install 10.10 - I was hoping I could delete the gamers edition to get back to my original single boot 10.10.

Hope the above makes sense.  Let me know if there;s any other info you need.  Cheers guys.  Thanks.

---

### Post by TheMadMan on 2010-12-05
Can anybody offer any assistance on this?  Thanks.

---

### Post by sikander3786 on 2010-12-05
I guess there are a few problems.

You installed gamers edition after the original 10.0 install so it is most likely that previous Grub got replaced with the one from new install. So after you delete the gamer's edition partition, you'll need to re-install Grub as mentioned here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Deleting the other parition and restoring Grub will be enough to remove Gamer's Edition from your HDD.

Resizing the root partition is not recommended. I would recommend to create a new partition in the freed up space and mount that in Ubuntu.

If you want to resize your root partition,

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

If you don't feel confident with the steps mentioned above, it would be better to post the output of your bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us nearly everything about your setup. Partitions and Grub, whatever we need to know and thus advise more efficiently.

Please wrap your output with proper code tags # from post menu. [/code] at the end and [code] at the beginning.

---

### Post by TheMadMan on 2010-12-05
> **sikander3786 said:**
> I guess there are a few problems.

You installed gamers edition after the original 10.0 install so it is most likely that previous Grub got replaced with the one from new install. So after you delete the gamer's edition partition, you'll need to re-install Grub as mentioned here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Deleting the other parition and restoring Grub will be enough to remove Gamer's Edition from your HDD.

Resizing the root partition is not recommended. I would recommend to create a new partition in the freed up space and mount that in Ubuntu.

If you want to resize your root partition,

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

If you don't feel confident with the steps mentioned above, it would be better to post the output of your bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us nearly everything about your setup. Partitions and Grub, whatever we need to know and thus advise more efficiently.

Please wrap your output with proper code tags # from post menu. [/code] at the end and [code] at the beginning.

Many thanks.  I'll have a look at the links and report back.

---

### Post by TheMadMan on 2010-12-05
Here's the results from the boot loader script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

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

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   585,773,184   585,771,137  83 Linux
/dev/sda2         585,775,102   976,771,071   390,995,970   5 Extended
/dev/sda5         952,199,168   976,771,071    24,571,904  82 Linux swap / Solaris
/dev/sda6         585,775,104   937,250,815   351,475,712  83 Linux
/dev/sda7         937,252,864   952,188,927    14,936,064  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ee536118-1c4f-4ef8-8435-a4270ae3a1b3   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e2088ae6-392a-4fb5-8c76-f35d004bd8a3   swap                                     
/dev/sda6        cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa   ext4                                     
/dev/sda7        3f6c3d83-10b8-4abe-805d-ea85e8e777ea   swap                                     
/dev/sda: PTTYPE="dos" 

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
search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=ee536118-1c4f-4ef8-8435-a4270ae3a1b3 ro   quiet splash nomodeset video=uvesafb:mode_option=,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=ee536118-1c4f-4ef8-8435-a4270ae3a1b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa ro single
	initrd /boot/initrd.img-2.6.35-23-generic-pae
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
# / was on /dev/sda1 during installation
UUID=ee536118-1c4f-4ef8-8435-a4270ae3a1b3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e2088ae6-392a-4fb5-8c76-f35d004bd8a3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.8GB: boot/grub/core.img
 288.3GB: boot/grub/grub.cfg
  88.7GB: boot/initrd.img-2.6.35-23-generic
  28.7GB: boot/vmlinuz-2.6.35-23-generic
  88.7GB: initrd.img
  28.7GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ee536118-1c4f-4ef8-8435-a4270ae3a1b3 ro quiet splash nomodeset video=uvesafb:mode_option=,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ee536118-1c4f-4ef8-8435-a4270ae3a1b3 ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ee536118-1c4f-4ef8-8435-a4270ae3a1b3 ro quiet splash nomodeset video=uvesafb:mode_option=,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee536118-1c4f-4ef8-8435-a4270ae3a1b3
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ee536118-1c4f-4ef8-8435-a4270ae3a1b3 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=cc5bee2b-e0fa-4b7d-b557-ae3f780c43fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=3f6c3d83-10b8-4abe-805d-ea85e8e777ea none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 398.8GB: boot/grub/core.img
 338.7GB: boot/grub/grub.cfg
 303.1GB: boot/initrd.img-2.6.35-23-generic-pae
 398.8GB: boot/vmlinuz-2.6.35-23-generic-pae
 303.1GB: initrd.img
 398.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  66 c6 8b 5f 91 21 6d f1  cd 09 94 29 d4 4f 55 32  |f.._.!m....).OU2|
00000010  80 ac 2b e9 3f 13 23 f8  4d 10 46 2f 1f b7 93 6a  |..+.?.#.M.F/...j|
00000020  ce ef b3 39 8a f2 ce 70  63 3f 49 1a a3 74 e5 14  |...9...pc?I..t..|
00000030  5e 10 a7 a5 cd fd 72 36  9a 2c 11 1c 30 dc d7 ad  |^.....r6.,..0...|
00000040  11 a2 a4 f8 8b ec 6c 13  79 5b 2f 0b 16 73 c2 2b  |......l.y[/..s.+|
00000050  ae 08 72 60 41 c4 78 a2  bd 3b ae 33 ca c8 fe 2b  |..r`A.x..;.3...+|
00000060  0c 9a d3 ef 9f c6 b3 2b  a2 ea 5c a8 4a e8 42 ef  |.......+..\.J.B.|
00000070  12 6e d5 9d d2 8d 84 ec  c8 9e 47 74 c4 7d 98 05  |.n........Gt.}..|
00000080  77 cc 60 b5 e5 83 05 95  41 4a 8d 14 78 09 7d 3b  |w.`.....AJ..x.};|
00000090  c7 7b b2 9d 03 b4 01 81  05 01 16 b2 63 3d 71 0c  |.{..........c=q.|
000000a0  0a 60 2c 57 67 a1 a2 0e  49 c8 35 83 c9 bc ea 8b  |.`,Wg...I.5.....|
000000b0  7d d8 6e b3 0e 1d cf 32  95 e8 a8 25 fb 6e 00 9b  |}.n....2...%.n..|
000000c0  56 c8 dd 82 58 69 29 9e  cb 31 51 17 e8 16 ae ee  |V...Xi)..1Q.....|
000000d0  f9 cb f1 44 56 57 6d 35  06 e2 71 d5 a2 44 fc d8  |...DVWm5..q..D..|
000000e0  10 f8 d8 aa 8d aa 4e 2b  2c db b5 53 32 4b 6a c2  |......N+,..S2Kj.|
000000f0  32 3d 25 bd ed ba 76 8d  d2 95 10 b1 0c 43 49 38  |2=%...v......CI8|
00000100  37 d8 6a 2a e0 bd 9b 73  97 11 ae dc ea 7a 0d f9  |7.j*...s.....z..|
00000110  87 98 f0 cb bf 24 c7 0a  4b bd e1 99 c2 7a a5 c1  |.....$..K....z..|
00000120  fb fb 37 61 94 9d 25 5b  f8 94 d1 41 a5 d3 37 f3  |..7a..%[...A..7.|
00000130  c0 e6 69 3a 37 47 47 25  51 78 2e 1c 32 4a 10 f1  |..i:7GG%Qx..2J..|
00000140  9e df ec b3 a1 25 92 2b  9f de 38 bc 7c be f8 2c  |.....%.+..8.|..,|
00000150  1e fd 9b 4e 76 60 dc df  cb 74 d6 b1 60 39 a4 10  |...Nv`...t..`9..|
00000160  4d 71 04 7b cd 04 e0 a3  ff 6b 98 46 9d 2f dd 69  |Mq.{.....k.F./.i|
00000170  1d 00 2b 2d b4 59 b0 53  d8 17 c9 2a 90 dc 7a 69  |..+-.Y.S...*..zi|
00000180  a3 f9 28 6d 58 f3 c1 94  e3 74 07 5d 4b a3 86 a5  |..(mX....t.]K...|
00000190  f7 86 85 5b c9 0e 64 fc  35 af 5e f4 be 37 07 01  |...[..d.5.^..7..|
000001a0  f4 4d ac 8c 41 a4 c4 a1  bb d3 ca d2 c2 d4 1d 57  |.M..A..........W|
000001b0  68 34 96 49 7a 18 34 12  0a d6 b6 7f 29 68 00 fe  |h4.Iz.4.....)h..|
000001c0  ff ff 82 fe ff ff 02 30  d7 15 00 f0 76 01 00 fe  |.......0....v...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 18 f3 14 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

hope I've wrapped it correctly.

Thanks

---

### Post by sikander3786 on 2010-12-05
Ok. From the Ubuntu Live CD, delete sda6 and sda7 partitions completely. (I assume and am pretty sure gamer's edition is installed to sda6, you need to be sure as well or you are going to delete your original 10.10 install).

You can then resize and merge sda6 and sda7 to make up a single partition.

Then re-install Grub. Here are the commands.

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the second command, it is just sda without an integer and not sda1.

Reboot and hopefully, you'll be back in business.

Good Luck!

---

### Post by TheMadMan on 2010-12-05
> **sikander3786 said:**
> Ok. From the Ubuntu Live CD, delete sda6 and sda7 partitions completely. (I assume and am pretty sure gamer's edition is installed to sda6, you need to be sure as well or you are going to delete your original 10.10 install).

You can then resize and merge sda6 and sda7 to make up a single partition.

Then re-install Grub. Here are the commands.

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the second command, it is just sda without an integer and not sda1.

Reboot and hopefully, you'll be back in business.

Good Luck!

I'm assuming that I need to stick the 10.10 live cd in and follow the on-screen prompts? Many thanks for your time and advice.

---

### Post by sikander3786 on 2010-12-05
> **TheMadMan said:**
> I'm assuming that I need to stick the 10.10 live cd in and follow the on-screen prompts? Many thanks for your time and advice.
Yes definitely. You need to do those commands from Ubuntu Live CD Terminal.

---

