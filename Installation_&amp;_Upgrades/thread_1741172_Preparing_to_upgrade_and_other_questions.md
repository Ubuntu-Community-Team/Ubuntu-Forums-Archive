---
title: "Preparing to upgrade and other questions"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by GaryTheCat on 2011-04-27
Hello

I'd like to upgrade to 11.04 after I've tried it for a few weeks on a live cd.  I've done upgrades before successfully but never a fresh install and I think the partitions on my machine have gone awry somehow.

How I 'intended' to set my machine up was:

**HDD1**
120 ish GB - for windows

**HDD2**
500 ish GB - I'd hoped one partition for ubuntu and one for data to be shared between ubuntu and windows.

But I can't seem to make any sense of the partitions I'm left with.

**and now to the questions...**

1.  What output would 'you' need to make sense of my partitioning?

2.  Once it's sorted out, is it easy to specifiy which partition to put 11.04 in as a fresh install (i.e. to put 11.04 back into the same partition that 10.10 was in).

Many thanks

G

---

### Post by Hedgehog1 on 2011-04-28
Please boot off the LiveCD/LiveUSB, select 'TRY' (or do this from your running Ubuntu partition), and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by GaryTheCat on 2011-04-28
Here we go Hedge, there's quite a bit of it...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       449,819       449,757  de Dell Utility
/dev/sda2             450,560    21,422,079    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,422,080   229,195,767   207,773,688   7 HPFS/NTFS
/dev/sda4         229,195,776   234,438,655     5,242,880   f W95 Ext d (LBA)
/dev/sda5         229,197,824   234,438,655     5,240,832  dd Dell Media Direct


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   530,662,682   530,660,635   7 HPFS/NTFS
/dev/sdb2         530,663,422   874,369,023   343,705,602   5 Extended
/dev/sdb5         862,300,160   874,369,023    12,068,864  82 Linux swap / Solaris
/dev/sdb6         530,663,424   850,229,247   319,565,824  83 Linux
/dev/sdb7         850,231,296   862,287,871    12,056,576  82 Linux swap / Solaris
/dev/sdb3         874,369,024   976,769,023   102,400,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0710                              vfat       DellUtility                   
/dev/sda2        32CC880CCC87C895                       ntfs       RECOVERY                      
/dev/sda3        64F88B22F88AF21A                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3290-413D                              vfat       MEDIADIRECT                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B82C12362C11EFDC                       ntfs       Data                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        9AC0CFDFC0CFC02D                       ntfs       Ubuntu                        
/dev/sdb5        9fb5a1fb-cab2-47c5-bb34-5eeac4511fbe   swap                                     
/dev/sdb6        5a3a5718-bfe6-482a-9209-acf0a9bb4e3b   ext4                                     
/dev/sdb7        2adeb9d1-0767-48d6-b95d-d0ce4e2511ec   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /home/gary/MountedData   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 5a3a5718-bfe6-482a-9209-acf0a9bb4e3b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 64f88b22f88af21a
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3290-413d
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=5a3a5718-bfe6-482a-9209-acf0a9bb4e3b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=2adeb9d1-0767-48d6-b95d-d0ce4e2511ec none            swap    sw              0       0
# To mount Data partition of 500 GB drive
/dev/sdb1 /home/gary/MountedData ntfs-3g defaults 0 0

=================== sdb6: Location of files loaded by Grub: ===================


 291.1GB: boot/grub/core.img
 315.0GB: boot/grub/grub.cfg
 278.9GB: boot/initrd.img-2.6.32-25-generic
 277.7GB: boot/initrd.img-2.6.35-22-generic
 308.2GB: boot/initrd.img-2.6.35-23-generic
 370.1GB: boot/initrd.img-2.6.35-24-generic
 271.9GB: boot/initrd.img-2.6.35-25-generic
 346.2GB: boot/initrd.img-2.6.35-27-generic
 355.4GB: boot/initrd.img-2.6.35-28-generic
 291.9GB: boot/vmlinuz-2.6.32-25-generic
 291.9GB: boot/vmlinuz-2.6.35-22-generic
 292.1GB: boot/vmlinuz-2.6.35-23-generic
 291.3GB: boot/vmlinuz-2.6.35-24-generic
 291.3GB: boot/vmlinuz-2.6.35-25-generic
 291.7GB: boot/vmlinuz-2.6.35-27-generic
 291.9GB: boot/vmlinuz-2.6.35-28-generic
 355.4GB: initrd.img
 346.2GB: initrd.img.old
 291.9GB: vmlinuz
 291.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  3f 92 52 28 5c 00 1e 80  9d 00 0f 00 14 00 ec 6e  |?.R(\..........n|
00000010  09 01 09 64 a2 89 0b 2b  1f f2 c7 ca 18 e4 b2 8a  |...d...+........|
00000020  d9 c9 69 18 7f 39 3c 56  49 d7 78 10 3f 20 04 21  |..i..9<VI.x.? .!|
00000030  9c 86 42 00 b8 98 1b 98  03 24 60 c4 fd ff 74 fc  |..B......$`...t.|
00000040  e9 4a ca cb 1a fa d8 0a  b2 3a 19 4f 89 f2 29 1f  |.J.......:.O..).|
00000050  a5 aa 20 bf cf 3d b2 94  a5 6c 65 bf eb 37 af 90  |.. ..=...le..7..|
00000060  2b 1d 84 4d 47 f3 b0 c0  87 47 57 7c e2 74 33 12  |+..MG....GW|.t3.|
00000070  d2 80 dd b9 41 b8 67 c3  85 ea e0 0b 80 2f 02 80  |....A.g....../..|
00000080  0b 40 2e 21 00 3f 01 d7  c9 41 0c ad fb 1e 84 ec  |.@.!.?...A......|
00000090  13 b8 b7 ab 40 0a 55 c7  39 3f 6b ca 48 4f e2 9a  |....@.U.9?k.HO..|
000000a0  f6 fa 12 57 25 73 15 47  ea 00 1c 80 64 90 06 40  |...W%s.G....d..@|
000000b0  27 e9 43 a4 98 1a b4 71  cb 59 3a de 05 48 5d f7  |'.C....q.Y:..H].|
000000c0  c4 8e e9 40 96 bc 59 34  84 18 4d 02 80 54 98 03  |...@..Y4..M..T..|
000000d0  be 34 63 80 db f6 50 dd  f6 d8 47 f7 b3 01 30 61  |.4c...P...G...0a|
000000e0  0c 61 0c 98 03 b4 a7 a4  31 29 25 0d 1c 66 d6 40  |.a......1)%..f.@|
000000f0  50 37 8d 19 ed 89 a5 60  c6 e2 ed 04 00 e5 31 69  |P7.....`......1i|
00000100  0d d8 32 2e 00 c4 33 86  00 68 03 a4 80 84 35 90  |..2...3..h....5.|
00000110  37 39 0b 0b af df 7b c1  80 65 55 30 03 5e c4 24  |79....{..eU0.^.$|
00000120  60 28 78 08 40 4f b6 c0  12 20 4e 1f 00 16 80 39  |`(x.@O... N....9|
00000130  01 3a 70 03 e0 07 80 1a  06 80 4e 42 c5 a1 23 c0  |.:p.......NB..#.|
00000140  27 4f 23 75 0a 80 33 00  2a 47 00 c4 03 32 68 03  |'O#u..3.*G...2h.|
00000150  d0 18 80 a7 10 86 92 89  67 14 23 1d 00 6a 00 fc  |........g.#..j..|
00000160  86 80 1d 80 9c 34 bc b2  b2 40 b6 33 36 6f f0 9f  |.....4...@.36o..|
00000170  9c 4f 80 a0 60 04 fc 41  17 40 31 0d 08 26 60 c1  |.O..`..A.@1..&`.|
00000180  c9 dc 9d eb 5f 3f cb 60  a1 f5 53 91 ea ec 77 32  |...._?.`..S...w2|
00000190  a3 bb b9 f5 7b ad 5a de  b1 a5 6b b4 2e f9 95 ee  |....{.Z...k.....|
000001a0  ee 88 cf 7e a6 70 00 00  01 0e 1a 73 62 87 a6 91  |...~.p.....sb...|
000001b0  b1 2d 25 29 a1 2c 33 29  33 2d a3 3c 7f 5f 00 fe  |.-%).,3)3-.<._..|
000001c0  ff ff 82 fe ff ff 02 60  c4 13 00 28 b8 00 00 fe  |.......`...(....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 30 0c 13 00 00  |...........0....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by GaryTheCat on 2011-04-28
I did try to go ahead with the upgrade from the live CD but the option to replace 10.10 wasn't there.

How do I tell the installer to 'put 11.04 where 10.10 used to be'?

It seems that if I select sdb6 then it gets deselected when I go to click install and then I get an error message about root rights...

Confused so perhaps I'm best to wait and then upgrade in a month or two via update manager? 

G

---

