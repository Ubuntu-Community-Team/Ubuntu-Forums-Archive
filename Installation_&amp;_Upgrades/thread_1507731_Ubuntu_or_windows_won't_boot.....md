---
title: "Ubuntu or windows won't boot...."
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by Drags111 on 2010-06-11
So I JUST installed 10.04 on a new hard drive for the third time. I had it completely wipe the hard drive and install ubuntu itself (so i couldn't mess anything up). Well NOW it won't even boot up ubuntu much less my windows hd.

So the setup is, my first harddrive which is 640gb and has my windows on it, and then my second harddrive which is 80gb and has my freshly installed ubuntu 10.04 on it. Neither will load. I don't even get a loading screen, I just get a flashing line after my mobo's splash screen.

I ran some boot loader info script and one of the first lines was
```
No boot loader is installed in the MBR of /dev/sda
```

---

### Post by wilee-nilee on 2010-06-12
> **Drags111 said:**
> So I JUST installed 10.04 on a new hard drive for the third time. I had it completely wipe the hard drive and install ubuntu itself (so i couldn't mess anything up). Well NOW it won't even boot up ubuntu much less my windows hd.

So the setup is, my first harddrive which is 640gb and has my windows on it, and then my second harddrive which is 80gb and has my freshly installed ubuntu 10.04 on it. Neither will load. I don't even get a loading screen, I just get a flashing line after my mobo's splash screen.

I ran some boot loader info script and one of the first lines was
```
No boot loader is installed in the MBR of /dev/sda
```

Post the whole script read out in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by garvinrick4 on 2010-06-12
It is not unusual to have to reinstall your grub2 to sda so give wilee-nilee the text from the script you ran and he will give you the code to install. Not a problem.

---

### Post by wilee-nilee on 2010-06-12
> **garvinrick4 said:**
> It is not unusual to have to reinstall your grub2 to sda so give wilee-nilee the text from the script you ran and he will give you the code to install. Not a problem.

Thanks for the support but you know I'm just a boot fixer poser.;)

---

### Post by Drags111 on 2010-06-12
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdb2         204,796,620 1,250,242,559 1,045,445,940   f W95 Ext d (LBA)
/dev/sdb5         204,796,683 1,250,242,559 1,045,445,877   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b5e71de4-4253-4680-af84-4c1f77bb57f2   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e8f55b21-9007-4911-a641-9684117a465a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FCF8E275F8E22D98                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        B0F05A7DF05A4A2C                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b5e71de4-4253-4680-af84-4c1f77bb57f2
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
search --no-floppy --fs-uuid --set b5e71de4-4253-4680-af84-4c1f77bb57f2
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set b5e71de4-4253-4680-af84-4c1f77bb57f2
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b5e71de4-4253-4680-af84-4c1f77bb57f2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set b5e71de4-4253-4680-af84-4c1f77bb57f2
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b5e71de4-4253-4680-af84-4c1f77bb57f2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set b5e71de4-4253-4680-af84-4c1f77bb57f2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set b5e71de4-4253-4680-af84-4c1f77bb57f2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fcf8e275f8e22d98
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b5e71de4-4253-4680-af84-4c1f77bb57f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e8f55b21-9007-4911-a641-9684117a465a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.8GB: boot/grub/core.img
  73.1GB: boot/grub/grub.cfg
  21.8GB: boot/initrd.img-2.6.32-21-generic
  21.8GB: boot/vmlinuz-2.6.32-21-generic
  21.8GB: initrd.img
  21.8GB: vmlinuz

================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  32 e8 90 93 71 a4 e7 30  73 c3 6d 4c eb 8f 9f 32  |2...q..0s.mL...2|
00000010  bf f5 c5 ca e7 dc 6e 86  ae 9f 66 50 da ef 99 b9  |......n...fP....|
00000020  99 2b 4c fe 81 af 98 d8  c0 75 e6 82 db 5a 7e ab  |.+L......u...Z~.|
00000030  63 5f f9 9c f8 46 79 57  e5 62 2d 8d 8e 8e ce ff  |c_...FyW.b-.....|
00000040  7f fc 97 1c fc 0b a6 f6  be 80 02 48 0d ed 93 f9  |...........H....|
00000050  53 54 57 1e c5 fb 3e 54  c4 d8 a0 11 35 d1 aa a9  |STW...>T....5...|
00000060  54 2a 33 56 7e 49 a6 6a  2a 01 62 12 a3 46 93 49  |T*3V~I.j*.b..F.I|
00000070  64 dc a2 13 47 8d 63 d4  8a 12 17 e2 16 51 16 fd  |d...G.c......Q..|
00000080  de d7 4d db 34 dd 6c 0d  d8 ec fb 2a fb be 2f b2  |..M.4.l....*../.|
00000090  af 2a 2a c8 a2 88 8a 20  08 0a c8 26 30 df fb ba  |.**.... ...&0...|
000000a0  69 17 26 35 ff c0 50 fd  78 ef dd 7e 9f 73 be e7  |i.&5..P.x..~.s..|
000000b0  dc d7 0e 0e 53 0e 0e ff  3f fe 57 07 5b fe b1 d6  |....S...?.W.[...|
000000c0  32 99 88 44 c3 3d b6 63  0f cf 4d f6 da 89 c6 ed  |2..D.=.c..M.....|
000000d0  45 22 fc 38 e8 3f 03 5d  b6 a3 dd b6 93 c3 6f ae  |E".8.?.]......o.|
000000e0  f7 f6 d9 0e f4 d8 8e 0f  d8 8b 26 66 7c d5 6f 3b  |..........&f|.o;|
000000f0  3c 60 37 39 43 ea f1 90  ed c0 90 dd c4 8c 75 f4  |<`79C.........u.|
00000100  1a 18 b6 1b ff af eb e3  f6 e3 3a fd d7 a6 42 e4  |..........:...B.|
00000110  c5 94 d6 f7 cd f5 89 3f  58 17 12 bd 39 aa 3e a6  |.......?X...9.>.|
00000120  90 5a 2f c8 2e e6 10 fb  0f de 3a 33 73 dd d0 d0  |.Z/.......:3s...|
00000130  fe e3 f7 8e cd 16 d9 1b  8a ec c5 22 7b 13 dd 7f  |..........."{...|
00000140  bb e5 46 e7 56 ad 38 b0  e7 93 55 26 b3 ec 96 cf  |..F.V.8...U&....|
00000150  39 f7 be c8 e6 fd 29 9b  f7 39 9b 8f 8d 4e 5a 7e  |9.....)..9...NZ~|
00000160  b8 73 ef aa bf 7e 2a 3a  be 4a 7c c4 d2 70 df 66  |.s...~*:.J|..p.f|
00000170  d1 1e fc 6c 33 dc b5 fb  cf 96 7b 57 7f 74 70 d5  |...l3.....{W.tp.|
00000180  9f 7e 32 d9 7c f0 ed af  8f 19 7d 6e 3d 65 66 cd  |.~2.|.....}n=ef.|
00000190  99 fd 66 f2 c9 af 66 2b  f6 af 5b 7e e2 c5 df 4e  |..f...f+..[~...N|
000001a0  2c fa e8 94 f8 c3 33 dc  8a 33 a2 15 67 8c fe 72  |,.....3..3..g..r|
000001b0  f2 83 f7 0e 7f f1 8e d5  6a 53 91 f5 d0 db 00 fe  |........jS......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  e8 3b 88 ff ff 53 8b 19  8b 0a 8b d0 8b 02 d9 03  |.;...S..........|
00000010  d8 09 d9 43 18 d8 49 18  de c1 d9 43 30 d8 49 30  |...C..I....C0.I0|
00000020  de c1 d9 18 d9 03 d8 49  04 d9 43 18 d8 49 1c de  |.......I..C..I..|
00000030  c1 d9 43 30 d8 49 34 de  c1 d9 58 04 d9 03 d8 49  |..C0.I4...X....I|
00000040  08 d9 43 18 d8 49 20 de  c1 d9 43 30 d8 49 38 de  |..C..I ...C0.I8.|
00000050  c1 d9 58 08 d9 03 d8 49  0c d9 43 18 d8 49 24 de  |..X....I..C..I$.|
00000060  c1 d9 43 30 d8 49 3c de  c1 d9 58 0c d9 03 d8 49  |..C0.I<...X....I|
00000070  10 d9 43 18 d8 49 28 de  c1 d9 43 30 d8 49 40 de  |..C..I(...C0.I@.|
00000080  c1 d9 58 10 d9 03 d8 49  14 d9 43 18 d8 49 2c de  |..X....I..C..I,.|
00000090  c1 d9 43 30 d8 49 44 de  c1 d9 58 14 d9 43 04 d8  |..C0.ID...X..C..|
000000a0  09 d9 43 1c d8 49 18 de  c1 d9 43 34 d8 49 30 de  |..C..I....C4.I0.|
000000b0  c1 d9 58 18 d9 43 04 d8  49 04 d9 43 1c d8 49 1c  |..X..C..I..C..I.|
000000c0  de c1 d9 43 34 d8 49 34  de c1 d9 58 1c d9 43 04  |...C4.I4...X..C.|
000000d0  d8 49 08 d9 43 1c d8 49  20 de c1 d9 43 34 d8 49  |.I..C..I ...C4.I|
000000e0  38 de c1 d9 58 20 d9 43  04 d8 49 0c d9 43 1c d8  |8...X .C..I..C..|
000000f0  49 24 de c1 d9 43 34 d8  49 3c de c1 d9 58 24 d9  |I$...C4.I<...X$.|
00000100  43 04 d8 49 10 d9 43 1c  d8 49 28 de c1 d9 43 34  |C..I..C..I(...C4|
00000110  d8 49 40 de c1 d9 58 28  d9 43 04 d8 49 14 d9 43  |.I@...X(.C..I..C|
00000120  1c d8 49 2c de c1 d9 43  34 d8 49 44 de c1 d9 58  |..I,...C4.ID...X|
00000130  2c d9 43 08 d8 09 d9 43  20 d8 49 18 de c1 d9 43  |,.C....C .I....C|
00000140  38 d8 49 30 de c1 d9 58  30 d9 43 08 d8 49 04 d9  |8.I0...X0.C..I..|
00000150  43 20 d8 49 1c de c1 d9  43 38 d8 49 34 de c1 d9  |C .I....C8.I4...|
00000160  58 34 d9 43 08 d8 49 08  d9 43 20 d8 49 20 de c1  |X4.C..I..C .I ..|
00000170  d9 43 38 d8 49 38 de c1  d9 58 38 d9 43 08 d8 49  |.C8.I8...X8.C..I|
00000180  0c d9 43 20 d8 49 24 de  c1 d9 43 38 d8 49 3c de  |..C .I$...C8.I<.|
00000190  c1 d9 58 3c d9 43 08 d8  49 10 d9 43 20 d8 49 28  |..X<.C..I..C .I(|
000001a0  de c1 d9 43 38 d8 49 40  de c1 d9 58 40 d9 43 08  |...C8.I@...X@.C.|
000001b0  d8 49 14 d9 43 20 d8 49  2c de c1 d9 43 38 00 fe  |.I..C .I,...C8..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 f5 3c 50 3e 00 00  |......?....<P>..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-06-12
From a quick look it seems that you have windows inside a extended partition is this correct?

The good thing is within a couple of hours a regular who is helpful will be on line, if time repeats itself.

But in the mean time we can work out some things possibly.

---

### Post by alexshr on 2010-06-12
Seems like your grub is installed in /dev/sdb

Why don't you try this command, insert the bootable CD of Ubuntu.
then run the ubuntu from LiveCD.

when boot up is complete, fire Terminal.

then use this command to load grub. 

# [B]sudo grub-install /dev/sdb

[/B]Why don't you try installing boot-loader to /dev/sda.

use following command to install grub in /dev/sda.
[B]
# sudo grub-install /dev/sda
[/B]

---

### Post by wilee-nilee on 2010-06-12
> **alexshr said:**
> Seems like your grub is installed in /dev/sdb

Why don't you try this command, insert the bootable CD of Ubuntu.
then run the ubuntu from LiveCD.

when boot up is complete, fire Terminal.

then use this command to load grub. 

**grub-install /dev/sdb**

Grub is already installed in sdb mbr, it appears that windows is inside a extended partition. If you look at the script the Linux kernels are showing, in grub.cfg.

---

### Post by wilee-nilee on 2010-06-12
> **alexshr said:**
> Seems like your grub is installed in /dev/sdb

Why don't you try this command, insert the bootable CD of Ubuntu.
then run the ubuntu from LiveCD.

when boot up is complete, fire Terminal.

then use this command to load grub. 

# [B]sudo grub-install /dev/sdb

[/B]Why don't you try installing boot-loader to /dev/sda.

use following command to install grub in /dev/sda.
[B]
# sudo grub-install /dev/sda
[/B]

Your edit still is incorrect with no mount of the sda partition, and no consideration of W7 being in a extended.

The correct way to load grub is this one so stop editing and messing with this thread!!!!!!!
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Drags111 on 2010-06-12
> **wilee-nilee said:**
> Your edit still is incorrect with no mount of the sda partition, and no consideration of W7 being in a extended.

The correct way to load grub is this one so stop editing and messing with this thread!!!!!!!
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

IDK what extended partition means. I just allowed windows 7 to install itself on the entire hard drive. And yes I'm running of the live CD now. Its the only way I can use my computer now sadly.

---

### Post by Drags111 on 2010-06-12
Solved it! I had to change the order of the harddrives from my ubuntu one being first to my windows one. Now I get the boot screen that lets me choose! (did it in bios of course).

---

