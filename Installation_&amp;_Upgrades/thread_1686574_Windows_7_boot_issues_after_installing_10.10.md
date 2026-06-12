---
title: "Windows 7 boot issues after installing 10.10"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by RagnarIV on 2011-02-12
As I needed to access my cisco lab, I installed 10.10 on my system again. However it appears to have overwritten my windows boot loader and I can no longer get into Windows 7. I've tried to repair the windows installation to no avail. I've already run the drive detection script and I will post the contents below.  Also the main problem is that Grub2 does not detect the Windows installation and I cannot get it to detect it either by calling grub2-update or by manually editing the grub.cfg file.

---

### Post by RagnarIV on 2011-02-12
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 453267512 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
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

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    62,529,535    62,527,488   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,445,617,663 1,445,615,616  83 Linux
/dev/sdc2       1,445,619,710 1,465,147,391    19,527,682   5 Extended
/dev/sdc5       1,445,619,712 1,465,147,391    19,527,680  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0654CD8654CD7947                       ntfs       BootSSD                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D4FC04B8FC049740                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        e7226a01-8d5f-4b82-a2c6-4ba1d0830620   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry ‘Windows 7&#8242; {
set root=’(hd0,msdos0)’
chainloader +1
}
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
# / was on /dev/sdc1 during installation
UUID=1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=e7226a01-8d5f-4b82-a2c6-4ba1d0830620 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 232.0GB: boot/grub/core.img
 687.6GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
   1.2GB: boot/initrd.img-2.6.35-25-generic
 232.0GB: boot/vmlinuz-2.6.35-22-generic
 232.0GB: boot/vmlinuz-2.6.35-25-generic
   1.2GB: initrd.img
   1.2GB: initrd.img.old
 232.0GB: vmlinuz
 232.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  0f c1 80 f1 7c 03 c3 f5  5f be 03 df e5 e5 3c 0f  |....|..._.....<.|
00000010  01 fd 48 3c 04 0a 20 f0  10 2c 83 7c 1e 03 fb 50  |..H<.. ..,.|...P|
00000020  0c 07 80 fe fd 58 20 7a  51 f8 3c 04 07 70 b9 5a  |.....X zQ.<..p.Z|
00000030  b1 f4 03 65 ea 8b c7 b8  a1 3e 41 93 86 78 92 3d  |...e.....>A..x.=|
00000040  1d c6 79 53 89 c0 ff ed  b7 f8 5a 38 72 bf 82 46  |..yS......Z8r..F|
00000050  de 3d e2 36 22 40 07 d0  82 24 aa 1e 2a ff bd b1  |.=.6"@...$..*...|
00000060  45 57 ff f6 26 81 90 30  90 01 a0 c2 48 90 0c 01  |EW..&..0....H...|
00000070  c0 d0 4a 12 02 0e 7d 57  ac cf fb de 94 07 09 1f  |..J...}W........|
00000080  fe 46 f0 c8 3c 04 1a e0  f0 1f cf 83 02 08 28 40  |.F..<.........(@|
00000090  3c 19 40 fa 8e 8b 86 2e  0a 66 20 c2 58 35 08 41  |<.@......f .X5.A|
000000a0  08 03 07 ff 12 81 a0 92  3d 00 c5 34 bc 48 1d 65  |........=..4.H.e|
000000b0  9b d9 be 97 27 c8 95 8f  fd f0 65 61 04 03 87 e1  |....'.....ea....|
000000c0  05 5f 87 e5 e1 03 f0 14  02 58 41 f8 1f a2 42 d4  |._.......XA...B.|
000000d0  ba ff 47 87 81 e0 20 41  07 80 81 24 18 bd 58 31  |..G... A...$..X1|
000000e0  78 30 90 a8 4b 2f a0 75  4f dc a3 b2 9f 73 c2 9e  |x0..K/.uO....s..|
000000f0  08 30 1e 07 fe 7f 80 65  55 e0 0e e4 56 a5 4d 87  |.0.....eU...V.M.|
00000100  db f8 88 03 81 e0 3e fd  07 80 fe d4 1b 01 82 00  |......>.........|
00000110  30 20 0f c7 e0 1c 01 82  47 fc 3c 8a 94 28 03 2e  |0 ......G.<..(..|
00000120  06 f8 1e 1e a9 56 a9 99  aa fd 18 fb 63 22 ef 3c  |.....V......c".<|
00000130  7f f7 05 3c 1b c2 48 94  01 c0 1d 44 b0 62 f5 65  |...<..H....D.b.e|
00000140  e2 5d aa e4 54 ac 7d ed  b2 a8 48 4c 0c 25 03 4a  |.]..T.}...HL.%.J|
00000150  10 82 1a a0 43 06 51 42  07 bf dd 1f f3 59 d3 76  |....C.QB.....Y.v|
00000160  cf 45 20 c5 54 18 c8 3c  04 14 20 f0 1f c5 83 17  |.E .T..<.. .....|
00000170  83 04 31 f7 82 14 1f 4a  10 80 38 7f cf d5 5c c1  |..1....J..8...\.|
00000180  d3 24 cf da 78 29 d8 2f  56 24 c0 86 0a 3d 55 fa  |.$..x)./V$...=U.|
00000190  cd 55 e5 51 08 31 ef 51  fd 2e 4e e0 78 08 44 41  |.U.Q.1.Q..N.x.DA|
000001a0  e0 20 33 07 80 fe e4 18  7e 0c 10 04 bd 2e 2f f8  |. 3.....~...../.|
000001b0  fc 4a 57 8a 4b 8b e9 f0  60 0e 06 08 40 c1 00 fe  |.JW.K...`...@...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 29 01 00 00  |............)...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by theozzlives on 2011-02-12
Have you tried:
```
sudo update-grub
```
?????

---

### Post by Rubi1200 on 2011-02-12
The grub.cfg file is missing the entry for Windows, so update-grub is unlikely to work.

The first thing to try is putting the boot flag back on sda. It is currently on sdc (indicated by an asterisk next to the partition). Best to do this from a LiveCD and then on the Windows partition using GParted right-click > Manage Flags. Take it off sdc as Linux does not need it and put it on for Windows. Reboot, try update-grub again and see if it helps.

In other words,
this:
> /dev/sdc1    * 

should be this:
> /dev/sd[COLOR=Red]a[/COLOR]1    * 

---

### Post by RagnarIV on 2011-02-12
I'll try updating the flags as soon as I get home. I'm working some OT till 11pm eastern.

---

### Post by wilee-nilee on 2011-02-12
sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

Your missing the highlighted files. As suggested put the bootflag on the partition=sda1, and run the autorepair as many as three times, from a booted W7 recovery or install disc. Here is a recovery if you need one.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

So after you get windows booting correctly you will put the sdc disc first to be read in the bios and install the grub bootloader to it. This will boot Ubuntu and W7.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

This link says reinstalling as most of the time there is some bootloader in the mbr, yours is empty per the script in sdc.
=> No boot loader is installed in the MBR of /dev/sdc

---

### Post by RagnarIV on 2011-04-12
It was the flags. I had to flag the Windows 7 partition as bootable.

---

