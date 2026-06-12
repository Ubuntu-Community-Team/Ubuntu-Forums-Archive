---
title: "XP will not boot after install Lucid"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by DJI274 on 2010-07-21
After installing lucid, if I select xp at startup all that appears is a flashing cursor. I have read other threads that report the same symptoms but I'n not familiar enough with grub to tell if I have the same problem. Below is output from boot info script, I would appreciate any help in fixing the problem.
<code>
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 187402275 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 187309611 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    62,830,214    62,830,152   7 HPFS/NTFS
/dev/sda2          62,830,276   214,885,439   152,055,164   5 Extended
/dev/sda5          62,830,278   141,821,819    78,991,542  83 Linux
/dev/sda6         141,821,883   197,246,069    55,424,187  83 Linux
/dev/sda7         197,246,133   199,559,429     2,313,297  82 Linux swap / Solaris
/dev/sda8         199,559,493   214,885,439    15,325,947  83 Linux
/dev/sda3         214,885,440   234,436,544    19,551,105   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        06A5645F06145C37                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        3EC6-2E70                              vfat       HP_RECOVERY                   
/dev/sda5        8a2d563a-a389-424a-8ebb-42c07e20cf0c   ext4                                     
/dev/sda6        1df5647f-2374-4053-8bd4-92f629016990   ext4                                     
/dev/sda7        c9d25432-e020-439c-89be-4134a12e1205   swap                                     
/dev/sda8        ab4cfef0-0cbd-43a4-8d8a-00fb4d981b7e   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda8        /downloadpart            ext4       (rw)
/dev/sda5        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1df5647f-2374-4053-8bd4-92f629016990 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1df5647f-2374-4053-8bd4-92f629016990 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=1df5647f-2374-4053-8bd4-92f629016990 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=1df5647f-2374-4053-8bd4-92f629016990 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1df5647f-2374-4053-8bd4-92f629016990 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1df5647f-2374-4053-8bd4-92f629016990 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1df5647f-2374-4053-8bd4-92f629016990
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 06a5645f06145c37
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda3)" {
	insmod fat
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3ec6-2e70
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda8       /downloadpart   ext4    defaults        0       2
/dev/sda5       /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=c9d25432-e020-439c-89be-4134a12e1205 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  94.3GB: boot/grub/core.img
  94.2GB: boot/grub/grub.cfg
  94.6GB: boot/initrd.img-2.6.32-21-generic
  94.8GB: boot/initrd.img-2.6.32-22-generic
  94.9GB: boot/initrd.img-2.6.32-23-generic
  94.6GB: boot/vmlinuz-2.6.32-21-generic
  73.4GB: boot/vmlinuz-2.6.32-22-generic
  93.1GB: boot/vmlinuz-2.6.32-23-generic
  94.9GB: initrd.img
  94.8GB: initrd.img.old
  93.1GB: vmlinuz
  73.4GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  6b d1 6a 2f 14 c1 9f a0  2c 36 93 e3 ae 20 6c e1  |k.j/....,6... l.|
00000010  60 17 a5 d6 18 54 5b b1  df 06 3e a3 5c a2 40 03  |`....T[...>.\.@.|
00000020  d2 7f 21 a4 6d 91 3a b2  04 09 d5 12 3e 59 28 07  |..!.m.:.....>Y(.|
00000030  22 59 37 12 99 ee ca 9f  13 63 5b 95 34 b5 dd b4  |"Y7......c[.4...|
00000040  73 a8 36 8f a0 d5 26 cb  38 d5 2e 03 bc 74 08 4a  |s.6...&.8....t.J|
00000050  66 a6 40 ed 11 72 09 80  f0 b4 ed 7b dc 5f 61 c0  |f.@..r.....{._a.|
00000060  ae 10 2b f3 7c fe 07 1b  87 a8 17 c0 01 bf 68 68  |..+.|.........hh|
00000070  e8 be d7 39 7e 85 5d 4f  a2 30 d7 90 9e 5e 58 97  |...9~.]O.0...^X.|
00000080  c3 da 00 3b 0f 6a 00 0a  55 a1 b8 1c ec 1e 41 7c  |...;.j..U.....A||
00000090  a8 29 76 a1 23 80 5e 3b  b9 f1 d5 dc af 7d 8b ed  |.)v.#.^;.....}..|
000000a0  cb dd 3e bc 15 0a 67 83  85 ee f6 d7 05 b1 3f 57  |..>...g.......?W|
000000b0  b7 15 29 ee ac 15 d7 d4  80 2b 07 6b f1 28 b2 ec  |..)......+.k.(..|
000000c0  3a c7 1c 14 47 3c aa 35  30 d7 b3 f7 3b 3d 5f f0  |:...G<.50...;=_.|
000000d0  6e f5 3c 09 4d db 12 9e  d7 15 78 e7 1b b9 4a 56  |n.<.M.....x...JV|
000000e0  41 30 00 34 e0 07 21 0c  14 fd 9e 93 64 81 58 60  |A0.4..!.....d.X`|
000000f0  94 18 23 98 14 03 80 29  b1 ad ad 75 45 cb b9 8e  |..#....)...uE...|
00000100  84 37 b1 bf 7f 4c ca a0  91 b8 95 60 39 3c 6e 5c  |.7...L.....`9<n\|
00000110  75 e8 30 de e0 a5 8e 03  37 cb b4 ff bd 25 f9 1c  |u.0.....7....%..|
00000120  16 8e 0e 92 d1 92 3a f9  74 f4 84 df e5 e7 d2 27  |......:.t......'|
00000130  cc f5 93 88 57 cd bd 57  51 9b 24 b1 24 2c db d2  |....W..WQ.$.$,..|
00000140  f3 73 0a fa 2e bf c9 78  b1 ae 64 40 ac 3d c9 9d  |.s.....x..d@.=..|
00000150  3a 85 0b 59 25 3e c7 a9  8e fe 8f 42 ac 96 66 31  |:..Y%>.....B..f1|
00000160  e2 3a 96 08 3e 55 f4 e3  42 4e a0 51 50 4d ce c2  |.:..>U..BN.QPM..|
00000170  c9 aa b8 e7 3b 60 c1 24  da e2 49 72 4e 49 fd ed  |....;`.$..IrNI..|
00000180  86 8a d3 63 52 fb 6a d9  15 2f 13 55 98 32 83 13  |...cR.j../.U.2..|
00000190  34 67 30 cb 62 5f 0d cd  d2 a3 78 4d 62 aa e4 14  |4g0.b_....xMb...|
000001a0  d3 40 2c 19 39 4a cd 15  8a 27 56 c3 73 21 67 a3  |.@,.9J...'V.s!g.|
000001b0  15 cb 67 74 f4 00 12 78  65 e1 a6 fc 00 12 00 fe  |..gt...xe.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 b6 50 b5 04 00 fe  |...........P....|
000001d0  ff ff 05 fe ff ff b8 50  b5 04 fa b4 4d 03 00 00  |.......P....M...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
</code>

---

### Post by oldfred on 2010-07-21
Boot sector info: [COLOR=Red] Grub 2 is installed in the boot sector of sda1[/COLOR] and
Boot sector info: [COLOR=Red] Grub 2 is installed in the boot sector of sda3[/COLOR]

sda1 is your windows and windows has to have the rest of its boot loader in the boot sector. You should also repair sda3 but that is not currently set to boot with the boot flag. sda3 looks like the recovery partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by DJI274 on 2010-07-21
Thanks Oldfred, that worked for me.

---

