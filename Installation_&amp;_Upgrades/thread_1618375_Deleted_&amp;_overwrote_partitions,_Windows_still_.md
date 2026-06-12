---
title: "Deleted &amp; overwrote partitions, Windows still can read/write files on the partitions?"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by House101 on 2010-11-10
I used to have several partitions with media files on them, but when I reinstalled ubuntu I had to overwrite them. Windows was hibernated during the process (grub was broken and I couldn't get in to shut it off). I've already logged in and out of ubuntu several times and the only partitions it sees are the Windows partition and itself, but when I logged back into Windows it still sees the 2 overwritten partitions (it could never see the ubuntu partition because its an ext3 or 4) and all the files on it are still intact and readable (even itunes can play them). The only way I can explain this is that Windows created a copy of the partitions and files and is now redirecting the OS there. How can this happen? And if that is what happened where would it be stored? This is freaking me out... did my hard drive grow an imagination? o_O

thanks

---

### Post by sikander3786 on 2010-11-11
Not sure about how that is possible.

From Ubuntu, can you please post the output of

```
sudo fdisk -l
```

---

### Post by Rubi1200 on 2010-11-11
I recommend you follow the instructions in the link at the bottom of my post.

Post the results back here so we can have a better overview of your current setup.

Thanks.

---

### Post by House101 on 2010-11-11
sikander3786:
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3834066b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29        2415    19173577+   7  HPFS/NTFS
/dev/sda2            4758        4864      852993    5  Extended
/dev/sda3            2416        4758    18817024   83  Linux
/dev/sda5            4758        4864      852992   82  Linux swap / Solaris

Partition table entries are not in disk order

```
Rubi1200:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        449,820    38,796,974    38,347,155   7 HPFS/NTFS
/dev/sda2          76,433,406    78,139,391     1,705,986   5 Extended
/dev/sda5          76,433,408    78,139,391     1,705,984  82 Linux swap / Solaris
/dev/sda3          38,797,312    76,431,359    37,634,048  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5290343090341CC3                       ntfs       SQ004203P01                   
/dev/sda2: PTTYPE="dos" 
/dev/sda3        80051196-83e6-4bbe-aa4d-0a7e1702e057   ext4                                     
/dev/sda5        c2fbab08-3838-4492-b497-2628b1a2b625   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 80051196-83e6-4bbe-aa4d-0a7e1702e057
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 80051196-83e6-4bbe-aa4d-0a7e1702e057
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 80051196-83e6-4bbe-aa4d-0a7e1702e057
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=80051196-83e6-4bbe-aa4d-0a7e1702e057 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 80051196-83e6-4bbe-aa4d-0a7e1702e057
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=80051196-83e6-4bbe-aa4d-0a7e1702e057 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 80051196-83e6-4bbe-aa4d-0a7e1702e057
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=80051196-83e6-4bbe-aa4d-0a7e1702e057 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 80051196-83e6-4bbe-aa4d-0a7e1702e057
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=80051196-83e6-4bbe-aa4d-0a7e1702e057 ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 80051196-83e6-4bbe-aa4d-0a7e1702e057
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 80051196-83e6-4bbe-aa4d-0a7e1702e057
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5290343090341cc3
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=80051196-83e6-4bbe-aa4d-0a7e1702e057 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c2fbab08-3838-4492-b497-2628b1a2b625 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  24.4GB: boot/grub/core.img
  31.2GB: boot/grub/grub.cfg
  21.2GB: boot/initrd.img-2.6.35-22-generic
  23.6GB: boot/initrd.img-2.6.35-23-generic
  24.4GB: boot/vmlinuz-2.6.35-22-generic
  24.6GB: boot/vmlinuz-2.6.35-23-generic
  23.6GB: initrd.img
  21.2GB: initrd.img.old
  24.6GB: vmlinuz
  24.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  fe 12 0e 01 30 ef fc 00  00 00 00 00 04 04 04 04  |....0...........|
00000010  10 13 0e 01 b0 d3 fc 00  00 00 00 00 04 04 04 04  |................|
00000020  32 13 0e 01 20 be fc 00  00 00 00 00 04 04 01 06  |2... ...........|
00000030  42 13 0e 01 f0 af fc 00  e0 a1 fc 00 01 06 04 04  |B...............|
00000040  62 13 0e 01 50 aa fc 00  00 00 00 00 02 02 04 04  |b...P...........|
00000050  72 13 0e 01 00 a2 fc 00  00 00 00 00 04 04 02 02  |r...............|
00000060  93 13 0e 01 60 d0 fc 00  e0 a1 fc 00 04 04 01 01  |....`...........|
00000070  a4 13 0e 01 d0 c8 fc 00  00 00 00 00 04 04 01 01  |................|
00000080  c2 13 0e 01 b0 e0 fc 00  00 00 00 00 02 02 04 04  |................|
00000090  d9 13 0e 01 60 d8 fc 00  00 00 00 00 04 04 02 02  |....`...........|
000000a0  20 35 fd 00 00 00 00 00  00 00 00 00 00 00 00 00  | 5..............|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  3e 30 0e 01 00 00 00 00  00 00 00 00 00 00 00 00  |>0..............|
000000f0  00 00 00 00 00 00 00 00  ff ff ff ff 01 00 00 00  |................|
00000100  56 00 00 00 60 e3 0c 01  60 ea 0c 01 00 00 00 00  |V...`...`.......|
00000110  60 f0 0c 01 00 00 00 00  60 e6 0c 01 00 00 00 00  |`.......`.......|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 bc fc 0c 01  |................|
00000130  06 fd 0c 01 60 fc 0c 01  01 00 00 00 05 19 0e 01  |....`...........|
00000140  60 ec 0c 01 60 f2 0c 01  48 00 00 00 54 00 00 00  |`...`...H...T...|
00000150  01 00 00 00 1c 3a 0e 01  8b 49 0e 01 a9 35 0e 01  |.....:...I...5..|
00000160  63 2c 0e 01 34 1b 0e 01  c6 17 0e 01 a9 3d 0e 01  |c,..4........=..|
00000170  94 14 0e 01 e0 35 0e 01  c8 17 0e 01 01 00 00 00  |.....5..........|
00000180  10 95 0e 01 4c 9a 0e 01  18 95 0e 01 20 95 0e 01  |....L....... ...|
00000190  28 95 0e 01 30 95 0e 01  38 95 0e 01 40 95 0e 01  |(...0...8...@...|
000001a0  48 95 0e 01 50 95 0e 01  1c 3a 0e 01 8b 49 0e 01  |H...P....:...I..|
000001b0  a9 35 0e 01 63 2c 0e 01  34 1b 0e 01 c6 17 00 fe  |.5..c,..4.......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 1a 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-11-11
A guess & why you should not hibernate if dual booting.

Windows has the old partition table and file index in memory. The Ubuntu install did not overwrite much data as it is not very large. So windows is overlapping the hard drive sectors with Ubuntu.

If you write anything into the media partitions, you will corrupt Ubuntu. You may actually be able to read much of the data but you are working like testdisk or photorec do in trying to recover data from absolute sectors.

---

### Post by House101 on 2010-11-12
thanks!

---

