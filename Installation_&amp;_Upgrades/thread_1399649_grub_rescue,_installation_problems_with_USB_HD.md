---
title: "grub rescue, installation problems with USB HD"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by bryanthemayan on 2010-02-05
So I am completely and utterly new to Linux, had it installed on my laptop's HD, wanted to move the installation over to my ext USB HD (300+ Gs) and was successful in doing so. 

However, (after a clean install) I was prompted to update the system. After updating and installing it asked me to restart. 

I restarted ubuntu, then was greeted with the grub rescue screen. 

I rebooted using the liveCD, this is what my boot info looks like:

```


============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=83ad0ff6-33d2-4a02-9f99-3a97d3530799)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d888d88

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,059,834    78,059,772   7 HPFS/NTFS
/dev/sda2          78,059,835   156,296,384    78,236,550   5 Extended
/dev/sda5    *     78,059,898    83,618,324     5,558,427  83 Linux
/dev/sda6         152,987,058   156,296,384     3,309,327  82 Linux swap / Solaris
/dev/sda7    *     83,618,388   150,047,099    66,428,712  83 Linux
/dev/sda8         150,047,163   152,986,994     2,939,832  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa6bf30d8

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         16,065   160,071,659   160,055,595   5 Extended
/dev/sdb5              16,128   160,071,659   160,055,532   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        06B890ADB8909CAD                       ntfs                                     
/dev/sda5        149f7af0-4cc7-4b15-ad94-dc1e5cb15143   ext4       Linux 2                       
/dev/sda6        2c11a738-c97c-4883-ba5e-064439a1179a   swap                                     
/dev/sda7        8d29266d-99c1-4351-94de-cccd524be995   ext4       Linux 1                       
/dev/sda8        85ed3ba3-d11e-4294-b3d4-8ef761d0b760   swap                                     
/dev/sdb5        56AC1ED1AC1EAC0D                       ntfs       Video Library                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=149f7af0-4cc7-4b15-ad94-dc1e5cb15143 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2c11a738-c97c-4883-ba5e-064439a1179a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  39.9GB: boot/vmlinuz-2.6.31-14-generic
  39.9GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 8d29266d-99c1-4351-94de-cccd524be995
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 8d29266d-99c1-4351-94de-cccd524be995
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=8d29266d-99c1-4351-94de-cccd524be995 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 8d29266d-99c1-4351-94de-cccd524be995
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=8d29266d-99c1-4351-94de-cccd524be995 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 8d29266d-99c1-4351-94de-cccd524be995
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8d29266d-99c1-4351-94de-cccd524be995 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 8d29266d-99c1-4351-94de-cccd524be995
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8d29266d-99c1-4351-94de-cccd524be995 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 06b890adb8909cad
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10 (9.10) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 149f7af0-4cc7-4b15-ad94-dc1e5cb15143
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=8d29266d-99c1-4351-94de-cccd524be995 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=85ed3ba3-d11e-4294-b3d4-8ef761d0b760 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  42.8GB: boot/grub/core.img
  42.8GB: boot/grub/grub.cfg
  42.8GB: boot/initrd.img-2.6.31-14-generic
  42.8GB: boot/initrd.img-2.6.31-17-generic
  42.8GB: boot/vmlinuz-2.6.31-14-generic
  42.8GB: boot/vmlinuz-2.6.31-17-generic
  42.8GB: initrd.img
  42.8GB: initrd.img.old
  42.8GB: vmlinuz
  42.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  d8 30 bf a6 00 00 00 00  |.........0......|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001d0  01 01 05 fe ff ff c1 3e  00 00 2b 41 8a 09 00 00  |.......>..+A....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

I'm able to see my HDs using the ls command, but not much else. Any suggestions or help would be appreciated.

---

### Post by bryanthemayan on 2010-02-06
I guess I'll get no help with this....I'm hoping to avoid just reinstalling XP and Ubuntu as I have quite a few personal setting on both I would hate to lose. 

Help? Anyone? Hello?

---

