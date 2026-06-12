---
title: "grub2 dual boot problem"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by vbdanl on 2011-11-19
hi.  i have a pc with ubuntu 11.10, fedora 16, and xp on it.  have been multi booting successfully for years.  ubuntu and fedora both have grub2.  
ubuntu is the primary boot mgr.  run update-grub on ubuntu and it finds all the OS's just fine.

problem is this pc requires acpi=off to boot.  in fedora in /boot/grub2/grub.cfg i see acpi=off in the menu entries. 
it is also in the /etc/default/grub GRUB_CMDLINE_LINUX line.

when ubuntu creates the menu entry for fedora, it does not contain the acpi=off info (also does not have quiet or rhgb either).

do i need to update something in ubuntu so when it builds the entry for fedora it will contain acpi=off, or do i need to change something in fedora so ubuntu will see it (acpi=off) and automatically include it when building the menu entry ?

i might also mention when i first booted fedora after install from live-cd (i had to reboot ubuntu and run update-grub so it would find the new fedora), it halted with a error "Warning no root device found" sda5.  looked like it was trying to use sde5 instead.  just rebooted and the next time it came up fine.  since then it seems like i get the same error after i run update-grub on ubuntu, then try to boot into fedora.  gets error, i reboot again, then it works.  figure somehow this is all related to the grub issues, but not really sure..

thanks for your help.

---

### Post by oldfred on 2011-11-19
I do not boot Fedora, so I am not sure. One workaround would be just to add your own entry to 40_custom, but you would have to manually update on each kernel update to Fedora. Does Fedora do like Ubuntu and put links in / (root) to the most recent kernel?

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

### Post by vbdanl on 2011-11-19
> **oldfred said:**
> I do not boot Fedora, so I am not sure. One workaround would be just to add your own entry to 40_custom, but you would have to manually update on each kernel update to Fedora. Does Fedora do like Ubuntu and put links in / (root) to the most recent kernel?

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk
no, fedora doesn't put the most recent kernel in root like ubuntu does, but maybe it is in /boot.
here is the results from bootinfoscript.sh
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 212898450 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Fedora release 16 (Verne) 
                       Kernel on an ()
    Boot files:        /etc/fstab /boot/grub2/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /menu.lst

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     11,100,915   185,598,944   174,498,030   7 NTFS / exFAT / HPFS
/dev/sda2                  63    11,100,914    11,100,852   b W95 FAT32
/dev/sda3         185,598,945   208,122,074    22,523,130  83 Linux
/dev/sda4         208,122,136   312,576,704   104,454,569   5 Extended
/dev/sda5         208,122,138   230,645,204    22,523,067  83 Linux
/dev/sda6         230,645,268   234,838,169     4,192,902  82 Linux swap / Solaris
/dev/sda7         234,838,233   312,576,704    77,738,472  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7410CE7810CE413A                       ntfs       
/dev/sda2        423B-2BDF                              vfat       RECOVERY
/dev/sda3        17d8d4aa-269a-4c3c-b086-a508ba58d63a   ext3       
/dev/sda5        bc44e92a-17c7-4850-bce1-4c5b71b41d98   ext4       _Fedora-16-i686-
/dev/sda6        733b305a-7dca-46bb-80b8-ea0a7a4fa595   swap       
/dev/sda7        adae4c97-e6b0-4c3d-a19c-c527b5def746   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 17d8d4aa-269a-4c3c-b086-a508ba58d63a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 17d8d4aa-269a-4c3c-b086-a508ba58d63a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/blue
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 17d8d4aa-269a-4c3c-b086-a508ba58d63a
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=17d8d4aa-269a-4c3c-b086-a508ba58d63a ro acpi=off  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 17d8d4aa-269a-4c3c-b086-a508ba58d63a
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=17d8d4aa-269a-4c3c-b086-a508ba58d63a ro recovery nomodeset acpi=off
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 17d8d4aa-269a-4c3c-b086-a508ba58d63a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 17d8d4aa-269a-4c3c-b086-a508ba58d63a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 7410CE7810CE413A
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Fedora release 16 (Verne) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root bc44e92a-17c7-4850-bce1-4c5b71b41d98
	linux /boot/vmlinuz-3.1.0-7.fc16.i686 root=/dev/sda5
	initrd /boot/initramfs-3.1.0-7.fc16.i686.img
}
menuentry "Fedora release 16 (Verne) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root bc44e92a-17c7-4850-bce1-4c5b71b41d98
	linux /boot/vmlinuz-3.1.1-1.fc16.i686 root=/dev/sda5
	initrd /boot/initramfs-3.1.1-1.fc16.i686.img
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
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=17d8d4aa-269a-4c3c-b086-a508ba58d63a /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=733b305a-7dca-46bb-80b8-ea0a7a4fa595 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  91.526756763 = 98.276106752   boot/grub/core.img                             1
  91.578674793 = 98.331853312   boot/grub/grub.cfg                             1
  91.651936054 = 98.410516992   boot/initrd.img-3.0.0-12-generic               6
  91.618969440 = 98.375119360   boot/vmlinuz-3.0.0-12-generic                  3
  91.651936054 = 98.410516992   initrd.img                                     6
  91.618969440 = 98.375119360   vmlinuz                                        3

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Fri Nov 18 14:52:41 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=bc44e92a-17c7-4850-bce1-4c5b71b41d98 /                       ext4    defaults        1 1
UUID=733b305a-7dca-46bb-80b8-ea0a7a4fa595 swap                    swap    defaults        0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 101.536747932 = 109.024252928  boot/initramfs-3.1.0-7.fc16.i686.img           1
 102.497754097 = 110.056125440  boot/initramfs-3.1.1-1.fc16.i686.img           2
 100.472813606 = 107.881862144  boot/vmlinuz-3.1.0-7.fc16.i686                 1
 102.245930672 = 109.785732096  boot/vmlinuz-3.1.1-1.fc16.i686                 1

================================ sda7/menu.lst: ================================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,4)
#          kernel /boot/vmlinuz-version ro root=/dev/sda5
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=9
splashimage=(hd0,4)/boot/grub/splash.xpm.gz
#hiddenmenu

title		Fedora (2.6.27.12-170.2.5.fc10.i686)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27.12-170.2.5.fc10.i686 ro root=UUID=35e6de3f-b9b5-4816-baef-94fd5c1d5ac4 rhgb quiet
initrd		/boot/initrd-2.6.27.12-170.2.5.fc10.i686.img

title		Fedora (2.6.27.5-117.fc10.i686)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=35e6de3f-b9b5-4816-baef-94fd5c1d5ac4 rhgb quiet
initrd		/boot/initrd-2.6.27.5-117.fc10.i686.img

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a0d98a09-fb61-4119-ab85-dde36c7b3aac ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a0d98a09-fb61-4119-ab85-dde36c7b3aac ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a0d98a09-fb61-4119-ab85-dde36c7b3aac ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP System Restore Disk
root		(hd0,1)
savedefault
makeactive
chainloader	+1
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 112.362411976 = 120.648221184  menu.lst                                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  b0 62 a9 00 44 2a 00 00  00 00 00 00 02 00 00 00  |.b..D*..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 df 2b 3b 42 20  20 20 20 20 20 20 20 20  |..).+;B         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  cc 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 53 54 4c 44 52 20 20  |.f..f.F..STLDR  |
000001b0  20 20 20 20 0d 0a 49 6e  76 61 6c 69 64 20 53 79  |    ..Invalid Sy|
000001c0  73 74 65 6d 20 44 69 73  6b 20 6f 72 0d 0a 44 69  |stem Disk or..Di|
000001d0  73 6b 20 49 2f 4f 20 65  72 72 6f 72 0d 0a 50 72  |sk I/O error..Pr|
000001e0  65 73 73 20 61 20 6b 65  79 20 74 6f 20 72 65 73  |ess a key to res|
000001f0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 55 aa  |tart..........U.|
00000200

Unknown BootLoader on sda4

00000000  01 00 00 00 01 00 02 00  64 62 6c 31 01 00 ff ff  |........dbl1....|
00000010  d0 ff ff ff 2d 00 33 00  2e 00 39 00 30 00 34 00  |....-.3...9.0.4.|
00000020  36 00 39 00 30 00 37 00  35 00 34 00 31 00 31 00  |6.9.0.7.5.4.1.1.|
00000030  30 00 39 00 37 00 45 00  2d 00 30 00 32 00 00 00  |0.9.7.E.-.0.2...|
00000040  e0 ff ff ff 76 6b 04 00  24 00 00 00 60 0a 02 00  |....vk..$...`...|
00000050  01 00 00 00 01 00 2e 00  64 62 6c 32 31 00 32 00  |........dbl21.2.|
00000060  d8 ff ff ff 30 00 2e 00  31 00 36 00 39 00 33 00  |....0...1.6.9.3.|
00000070  34 00 31 00 31 00 30 00  35 00 32 00 32 00 32 00  |4.1.1.0.5.2.2.2.|
00000080  37 00 30 00 32 00 00 00  e0 ff ff ff 76 6b 04 00  |7.0.2.......vk..|
00000090  04 00 00 80 32 00 00 00  01 00 00 00 01 00 04 00  |....2...........|
000000a0  64 62 6c 33 30 00 00 00  e0 ff ff ff 76 6b 04 00  |dbl30.......vk..|
000000b0  04 00 00 80 30 00 00 00  01 00 00 00 01 00 00 00  |....0...........|
000000c0  64 62 6c 34 30 00 00 00  f0 ff ff ff 43 00 4a 00  |dbl40.......C.J.|
000000d0  44 00 61 00 72 00 00 00  d8 ff ff ff 88 06 02 00  |D.a.r...........|
000000e0  90 07 02 00 d8 07 02 00  20 08 02 00 58 08 02 00  |........ ...X...|
000000f0  78 08 02 00 b8 08 02 00  d8 08 02 00 76 6b 04 00  |x...........vk..|
00000100  a0 ff ff ff 6e 6b 20 00  1e 26 ec 40 88 24 c7 01  |....nk ..&.@.$..|
00000110  00 00 00 00 80 0d 02 00  01 00 00 00 00 00 00 00  |................|
00000120  f8 08 02 00 ff ff ff ff  00 00 00 00 ff ff ff ff  |................|
00000130  c0 3d 07 00 ff ff ff ff  02 00 00 00 00 00 00 00  |.=..............|
00000140  00 00 00 00 00 00 00 00  1e 26 ec 40 0c 00 00 00  |.........&.@....|
00000150  50 72 65 53 68 69 66 74  49 6e 66 6f 00 00 00 00  |PreShiftInfo....|
00000160  d8 ff ff ff 6c 66 03 00  38 09 02 00 43 75 72 72  |....lf..8...Curr|
00000170  f0 04 02 00 50 6f 73 74  00 0b 02 00 50 72 65 53  |....Post....PreS|
00000180  00 00 00 00 00 00 00 00  a8 ff ff ff 6e 6b 20 00  |............nk .|
00000190  1e 26 ec 40 88 24 c7 01  00 00 00 00 00 0b 02 00  |.&.@.$..........|
000001a0  00 00 00 00 00 00 00 00  ff ff ff ff ff ff ff ff  |................|
000001b0  08 00 00 00 b8 74 02 00  c0 3d 07 00 ff ff 00 fe  |.....t...=......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 bb ac 57 01 00 fe  |............W...|
000001d0  ff ff 05 fe ff ff bd ac  57 01 c5 fa 3f 00 00 00  |........W...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by oldfred on 2011-11-19
The script did not show Fedora's grub file. Did they change the name or location? The script just has a long list of files & locations to look at like '/boot/grub2/grub.conf'.
I thought os-prober tried to find other menus and copy that and if not just build a simple boot config. It probably does not know to look for other parameters.

I would turn off os-prober and create my own boot stanza in 40_custom. You will have to manually update it for each kernel update in Fedora.

#Copy Fedora entry from this:
gedit /boot/grub/grub.cfg
#Copy into this and edit at will
gksudo gedit /etc/grub.d/40_custom
# then update Ubuntu's grub menu
sudo update-grub

To turn off os-prober:
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or you can just make it non-executeable:
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by vbdanl on 2011-11-19
thanks oldfred.  i added a 22_fedora line, basically the same as what you suggested in the 40 or 41 line, but it sorts sooner in the list.  think i will leave the 30 prober in for now if for no other reason to remind me of what the current fedora release actually is (then i can update the 22* file accordingly.
seems like there should be a way to get this to work by just editing the other regular files.. when i get some more time will probably experiment some more..
thanks again.

---

### Post by drs305 on 2011-11-19
> **vbdanl said:**
> 
seems like there should be a way to get this to work by just editing the other regular files.. when i get some more time will probably experiment some more..
thanks again.

It can be done but I won't say it's a lot easier.

When Grub 2 came out there were a lot of users wanting to customize the way it presented the menuentries, order, etc. Without any apps developed for this purpose yet, I made a thread with a lot of crude script modifications to accomplish various tweaks (I'm not much of a scripter).

Over time these alterations weren't necessary as apps such as Grub Customizer appeared. But the concept still remains, so I dusted off the thread and took a look.

You could modify the 30_os-prober script to add "acpi=off" to the 'linux' line of any menuentry title which includes "Fedora" as the first word. 

I'm using Grub 1.99, and the lines to modify occur around line 227 of /etc/grub.d/30_os-prober.

Be sure to make a backup of 30_os-prober before you start to modify it and check /boot/grub/grub.cfg to make sure the entries look correct before you reboot. Save the backup elsewhere or make it unexecutable so the prober doesn't run twice.

> 	found_other_os=1
        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" --class gnu-linux --class gnu --class os {
EOF
	save_default_entry | sed -e "s/^/\t/"
	if [ -z "${prepare_boot_cache}" ]; then
	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
	fi
	printf '%s\n' "${prepare_boot_cache}"

[B]	checkFedora="`echo ${LONGNAME} | cut -d ' ' -f 1`"

	if [ $checkFedora = "Fedora" ]; then
		cat <<  EOF
		linux ${LKERNEL} ${LPARAMS} acpi=off
EOF
	fi

	if [ ! $checkFedora = "Fedora" ]; then
		cat <<  EOF
		linux ${LKERNEL} ${LPARAMS}
EOF
	fi
[/B]
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
done


The thread referenced earlier is the "Tweaks" link in my signature line.

---

### Post by vbdanl on 2011-11-20
thanks drs305.  that worked perfectly.
i am now reading through your tweaks to find out how to change the Fedora entries to include the version#.  Currently my grub menu shows the 3 latest Fedora builds, but they all appear the same "Fedora release 16 (Verne) (on /dev/sda5)".  I want them to include "3.x.x.x-x" or whatever the build # is.

---

### Post by drs305 on 2011-11-20
> **vbdanl said:**
> thanks drs305.  that worked perfectly.
i am now reading through your tweaks to find out how to change the Fedora entries to include the version#.  Currently my grub menu shows the 3 latest Fedora builds, but they all appear the same "Fedora release 16 (Verne) (on /dev/sda5)".  I want them to include "3.x.x.x-x" or whatever the build # is.

Glad the initial solution worked.

I don't have various versions of Fedora installed - normally I can come up with solutions only when I can test them myself. I do have some various Slackware kernels, so if I can come up with something before you do I'll post it.

---

### Post by vbdanl on 2011-11-20
i got it to work by just adding:
LVER="`echo ${LKERNEL} | cut -c15-21'" and using LVER instead of LDEVICE which it was using.
am sure there is a better method than cut -c15-21 to pull out the version #, but it works good enough for me for now.
thanks again for your help.

---

### Post by drs305 on 2011-11-20
At least with Slackware, all I had to do was insert the LKERNEL variable within the menuentry title.

The actual LKERNEL variable includes some extraneous things like "/boot/" but you could create a new variable using the 'cut' command to shorten it to just the kernel number and insert that in the menuentry.

But to see what it comes up with initially, just insert LKERNEL in the menuentry (approximately line 229 of /etc/grub.d/30_os-prober).
This is what the result looks like for me:
> menuentry "Slackware Linux (Slackware 13.37.0) [COLOR="DarkRed"]/boot/vmlinuz-huge-2.6.37.6[/COLOR] (on /dev/sdb7)"

Here is the 30_os-prober change:
> menuentry "${LLABEL} [COLOR="DarkRed"]**${LKERNEL} **[/COLOR](on ${DEVICE})" --class gnu-linux --class gnu --class os {

---

