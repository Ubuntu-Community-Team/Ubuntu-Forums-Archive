---
title: "upgraded to 10.04 and existing xp partition won't load"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by lurch1363 on 2010-04-14
I recently upgraded to ubuntu 10.04 from 9.10.  I now have grub 1.98 and my problem is that when i select windows xp from grub it just goes to a black screen with a white flashing line.  If i boot ubuntu it does the same thing for about five seconds then ubuntu loads right up.  I hit e on windows xp in grub and this is what came up.  
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs--uuid --set 7a841c73841c33db
drivemap -s _hd0) ${root}
chainloader +1

I then hit c on windows xp and entered each line on its own and the only error was this.
error unknown argument '--fs-uuid'

any ideas?

---

### Post by gordintoronto on 2010-04-14
I suggest you ask in the Lucid Testing forum. It is still beta, so you should expect it to break.

---

### Post by oldfred on 2010-04-14
+1 for gordintoronto (if the admins see this post they may move it(

I have seen a lot of users that during the install selected to install grub all over the place and wiped out the part of the windows boot that  is in the windows partition.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by lurch1363 on 2010-04-14
here are the results
```
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 5027327 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 5027327 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda2 has 58593736 sectors, but according to the info 
                       from fdisk, it has 155830499 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 5027327 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 5027327 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

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

/dev/sda1                  63       401,496       401,434   3 XENIX usr
/dev/sda2    *        401,625   156,232,124   155,830,500   7 HPFS/NTFS
/dev/sda3         156,232,125   312,560,639   156,328,515   f W95 Ext d (LBA)
/dev/sda5         156,232,188   312,560,639   156,328,452   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   150,239,879   150,239,817  83 Linux
/dev/sdb2         150,239,880   156,248,189     6,008,310   5 Extended
/dev/sdb5         150,239,943   156,248,189     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8c9eb5c2-212b-4d03-b602-f4b7e3264b1c   ext3       /boot                         
/dev/sda2        7A841C73841C33DB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        A4E85050E850233A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ff85fd0b-ea5a-4049-b265-caeda3fcb7b8   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        994dd40a-0c3b-4729-9504-64c081122821   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/7A841C73841C33DB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/A4E85050E850233A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/_boot             ext3       (rw,nosuid,nodev,uhelper=udisks)


============================= sda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.23.15-137.fc8)
	root (hd0,0)
	kernel /vmlinuz-2.6.23.15-137.fc8 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.23.15-137.fc8.img
title Fedora (2.6.23.1-42.fc8)
	root (hd0,0)
	kernel /vmlinuz-2.6.23.1-42.fc8 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.23.1-42.fc8.img
title Other
	rootnoverify (hd1,0)
	chainloader +1

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.23.1-42.fc8.img
    .0GB: initrd-2.6.23.15-137.fc8.img
    .0GB: vmlinuz-2.6.23.1-42.fc8
    .0GB: vmlinuz-2.6.23.15-137.fc8

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ff85fd0b-ea5a-4049-b265-caeda3fcb7b8
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ff85fd0b-ea5a-4049-b265-caeda3fcb7b8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ff85fd0b-ea5a-4049-b265-caeda3fcb7b8
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=ff85fd0b-ea5a-4049-b265-caeda3fcb7b8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ff85fd0b-ea5a-4049-b265-caeda3fcb7b8
	echo	Loading Linux 2.6.32-19-generic ...
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=ff85fd0b-ea5a-4049-b265-caeda3fcb7b8 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ff85fd0b-ea5a-4049-b265-caeda3fcb7b8
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=ff85fd0b-ea5a-4049-b265-caeda3fcb7b8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ff85fd0b-ea5a-4049-b265-caeda3fcb7b8
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=ff85fd0b-ea5a-4049-b265-caeda3fcb7b8 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ff85fd0b-ea5a-4049-b265-caeda3fcb7b8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ff85fd0b-ea5a-4049-b265-caeda3fcb7b8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 7a841c73841c33db
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=ff85fd0b-ea5a-4049-b265-caeda3fcb7b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=994dd40a-0c3b-4729-9504-64c081122821 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
   8.3GB: boot/initrd.img-2.6.31-20-generic
  10.1GB: boot/initrd.img-2.6.32-19-generic
   6.5GB: boot/vmlinuz-2.6.31-20-generic
   8.3GB: boot/vmlinuz-2.6.32-19-generic
  10.1GB: initrd.img
   8.3GB: initrd.img.old
   8.3GB: vmlinuz
   6.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  1c 63 5e 2b bf f5 82 f0  0d 72 c1 84 d4 67 6f e2  |.c^+.....r...go.|
00000010  01 53 8d 0d 75 f1 75 75  54 79 3e 46 9e c8 62 75  |.S..u.uuTy>F..bu|
00000020  ee 9e 45 90 97 a9 5d 59  b9 85 dc c5 76 36 78 1d  |..E...]Y....v6x.|
00000030  02 7d 18 60 ef 48 de 3f  ef 5b 41 fc 08 f7 50 4e  |.}.`.H.?.[A...PN|
00000040  dc 1c 22 62 0c 14 16 16  74 34 6f 0f 6f 83 59 96  |.."b....t4o.o.Y.|
00000050  08 f2 7e 1e 1c 11 5f d8  78 b5 4f b9 6d 0d f7 6b  |..~..._.x.O.m..k|
00000060  a5 3b fc 9c dd 1c 7e ba  27 bd 74 2b 20 ed 69 69  |.;....~.'.t+ .ii|
00000070  f4 05 df 5b fa 24 ab 3a  47 e0 0c 26 a6 20 6f 26  |...[.$.:G..&. o&|
00000080  8c 27 5e 98 26 6c 2f 19  fe 49 44 07 8d 77 aa 7c  |.'^.&l/..ID..w.||
00000090  bd e2 d9 9e 4b c6 75 34  94 97 7e ce 42 6b 5b aa  |....K.u4..~.Bk[.|
000000a0  3e 24 df ab 6a 6a 31 29  97 a3 0c 4f f7 f4 94 07  |>$..jj1)...O....|
000000b0  97 0e ec d6 7f 3c 36 89  e3 cb fa 51 5f eb 47 de  |.....<6....Q_.G.|
000000c0  8c 97 3a b8 cf e7 ed 4f  a6 57 f5 f7 17 cf ef c1  |..:....O.W......|
000000d0  93 00 10 1b 7d 3d 8e 68  be 99 b8 a5 75 9a fe 32  |....}=.h....u..2|
000000e0  a3 c1 34 7d 39 ec 1e 97  8e 3b ef 0f ee 8f 97 ca  |..4}9....;......|
000000f0  64 ae 85 6c 1a ac 04 40  26 3f fa ba be ce d5 c0  |d..l...@&?......|
00000100  5c f6 e8 61 66 7e 3e 7e  48 ab 37 26 69 5a a8 9b  |\..af~>~H.7&iZ..|
00000110  bc f3 07 1f dc af f2 72  ee 62 7c 3a fe d6 24 a9  |.......r.b|:..$.|
00000120  b8 c5 fb f7 26 e0 43 6c  2e bf e0 9f eb ad 2b fc  |....&.Cl......+.|
00000130  d4 35 5f 1a 58 5a 42 06  25 48 2f 50 12 55 f1 bf  |.5_.XZB.%H/P.U..|
00000140  e0 ed 22 d3 39 96 89 3e  f4 2f 07 90 b6 92 3a 6b  |..".9..>./....:k|
00000150  26 e1 0a 52 1f ed cc f6  de 5d fe 20 0d fc b3 35  |&..R.....]. ...5|
00000160  33 0d 7e d8 14 f0 9a aa  ff cd fb 59 2a 1f 87 82  |3.~........Y*...|
00000170  19 d7 8f 84 d3 55 f0 f8  57 ad d0 27 1b 3b ec 6e  |.....U..W..'.;.n|
00000180  d4 73 31 5d e9 e2 db 05  e7 0f 7d e4 a6 e0 be 10  |.s1]......}.....|
00000190  63 b3 97 eb 3f 78 62 fd  62 df 03 2f 40 91 f8 e9  |c...?xb.b../@...|
000001a0  7c 11 c1 d7 94 6b a9 29  7d 3c 26 1d 5d 71 e7 f4  ||....k.)}<&.]q..|
000001b0  bd aa 1d f1 b3 9b 69 06  3f 48 91 b1 df 1f 00 01  |......i.?H......|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 04 62 51 09 00 00  |......?....bQ...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-04-14
During the install did you see a menu like I am attaching (from doug) and check off more than one box?

You installed grub to the windows PBR overwriting windows boot files.

Restore PBR boot sector for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

or the windows way - do not run fixmbr or you will have to reinstall grub to the MBR:
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)

---

### Post by lurch1363 on 2010-04-14
yes i just selected all and let grub sort it out, which in hindsight was a horrible idea.  going to try testdisk, and ill let you know how it goes.

---

### Post by lurch1363 on 2010-04-14
ran testdisk and used the guide you linked and it worked wonderfully.  So problem solved.

---

