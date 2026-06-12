---
title: "XP doesn't book after migrating from SUSE to UBUNTU 10.10"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by bertmung on 2010-11-03
I recently migrated from SuSE 11.2 to UBUNTU 10.10.

I didn't run into any major problems until I tried to boot into XP.

The screen just goes blank.

My search of other threads revealed error message problems but no blank screen problems.

Would it make sense to backup my home files, reinstall XP and then reinstall UBUNTU?

---

### Post by Rubi1200 on 2010-11-03
Hi,
please boot the computer with a LiveCD (any will do) or from within your Ubuntu install and post the results of the boot-script linked at the bottom of my post.

The information will hopefully tell us where the problem is and will make offering solutions easier.

Thanks.

---

### Post by bertmung on 2010-11-12
Here's the contents of RESULTS.txt

         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,179,686    40,179,624   7 HPFS/NTFS
/dev/sda2          40,179,710   234,440,703   194,260,994   5 Extended
/dev/sda5          40,179,712   229,836,799   189,657,088  83 Linux
/dev/sda6         229,838,848   234,440,703     4,601,856  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D034482C344817BC                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        27bf4199-8ca4-4afc-9f48-2df8aa2ca82f   ext4                                     
/dev/sda6        6460b7c2-04b6-4ca0-92b8-8e79f6361ffa   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A8C12EF8C12D573                       ntfs       NewVolume                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        f6563566-91ce-459e-91fc-7e350b6aa4f4   reiserfs   My Book                       
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/My Book           reiserfs   (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/NewVolume         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 27bf4199-8ca4-4afc-9f48-2df8aa2ca82f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 27bf4199-8ca4-4afc-9f48-2df8aa2ca82f
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 27bf4199-8ca4-4afc-9f48-2df8aa2ca82f
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=27bf4199-8ca4-4afc-9f48-2df8aa2ca82f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 27bf4199-8ca4-4afc-9f48-2df8aa2ca82f
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=27bf4199-8ca4-4afc-9f48-2df8aa2ca82f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 27bf4199-8ca4-4afc-9f48-2df8aa2ca82f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=27bf4199-8ca4-4afc-9f48-2df8aa2ca82f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 27bf4199-8ca4-4afc-9f48-2df8aa2ca82f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=27bf4199-8ca4-4afc-9f48-2df8aa2ca82f ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 27bf4199-8ca4-4afc-9f48-2df8aa2ca82f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 27bf4199-8ca4-4afc-9f48-2df8aa2ca82f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d034482c344817bc
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=27bf4199-8ca4-4afc-9f48-2df8aa2ca82f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6460b7c2-04b6-4ca0-92b8-8e79f6361ffa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  93.7GB: boot/grub/core.img
  44.4GB: boot/grub/grub.cfg
  40.4GB: boot/initrd.img-2.6.35-22-generic
  27.4GB: boot/initrd.img-2.6.35-23-generic
  93.7GB: boot/vmlinuz-2.6.35-22-generic
  93.7GB: boot/vmlinuz-2.6.35-23-generic
  27.4GB: initrd.img
  40.4GB: initrd.img.old
  93.7GB: vmlinuz
  93.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  74 63 40 51 2b 21 5a 39  2d a6 92 85 a3 87 7b 93  |tc@Q+!Z9-.....{.|
00000010  72 64 8d 6a 5b 8b 6d 5d  84 6c 61 54 30 25 5e 3e  |rd.j[.m].laT0%^>|
00000020  32 56 31 27 57 31 28 57  31 28 57 32 28 57 32 29  |2V1'W1(W1(W2(W2)|
00000030  58 33 29 58 33 2a 58 33  2a 59 34 2a 78 68 49 74  |X3)X3*X3*Y4*xhIt|
00000040  63 40 74 63 40 2c 8a 64  73 62 40 73 62 40 73 62  |c@tc@,.dsb@sb@sb|
00000050  40 73 62 40 73 62 40 73  62 40 73 62 40 73 62 40  |@sb@sb@sb@sb@sb@|
00000060  73 62 40 73 62 40 73 62  40 73 62 40 73 62 40 51  |sb@sb@sb@sb@sb@Q|
00000070  2b 21 67 4c 3d af 98 8d  a3 86 7a 93 72 63 8d 6a  |+!gL=.....z.rc.j|
00000080  5b 8b 6d 5d 82 6b 5f 51  2b 21 64 46 3a 5b 36 2d  |[.m].k_Q+!dF:[6-|
00000090  5b 36 2d 5b 36 2d 5b 37  2e 5c 37 2e 5c 37 2f 5c  |[6-[6-[7.\7.\7/\|
000000a0  38 2f 5d 38 2f 5d 39 30  77 67 49 73 62 40 6a 5f  |8/]8/]90wgIsb@j_|
000000b0  40 65 77 72 73 61 40 73  61 40 73 61 40 73 61 40  |@ewrsa@sa@sa@sa@|
000000c0  73 61 40 73 61 40 73 61  40 73 61 40 73 61 40 72  |sa@sa@sa@sa@sa@r|
000000d0  61 40 72 61 40 72 61 40  72 61 40 58 36 28 78 61  |a@ra@ra@ra@X6(xa|
000000e0  52 b2 9a 90 a2 86 7a 93  71 63 8d 6a 5b 8b 6d 5d  |R.....z.qc.j[.m]|
000000f0  82 6a 5e 51 2b 21 68 4a  3e 5f 3b 32 5f 3b 32 5f  |.j^Q+!hJ>_;2_;2_|
00000100  3b 33 60 3c 33 60 3c 34  60 3c 34 61 3d 34 61 3d  |;3`<3`<4`<4a=4a=|
00000110  35 61 3e 35 72 5d 46 65  5e 3f 57 5e 2b 64 77 72  |5a>5r]Fe^?W^+dwr|
00000120  72 61 3f 72 61 3f 72 61  3f 72 61 3f 72 61 3f 72  |ra?ra?ra?ra?ra?r|
00000130  61 3f 72 61 3f 72 61 3f  72 61 3f 72 61 3f 72 61  |a?ra?ra?ra?ra?ra|
00000140  3f 72 61 3f 72 61 3f 5d  3d 2d 86 71 62 b2 9a 90  |?ra?ra?]=-.qb...|
00000150  a2 85 79 92 71 63 8d 6a  5b 8b 6d 5d 83 6b 5f 52  |..y.qc.j[.m].k_R|
00000160  2c 22 67 49 3e 63 40 37  63 40 38 64 40 38 64 41  |,"gI>c@7c@8d@8dA|
00000170  39 64 41 39 65 41 39 65  42 3a 65 42 3a 66 43 3a  |9dA9eA9eB:eB:fC:|
00000180  6a 5d 44 56 5d 28 56 5d  28 64 77 72 71 60 3f 71  |j]DV](V](dwrq`?q|
00000190  60 3f 71 60 3f 71 60 3f  71 60 3f 71 60 3f 71 60  |`?q`?q`?q`?q`?q`|
000001a0  3f 71 60 3f 71 60 3f 71  60 3f 71 60 3f 71 60 3f  |?q`?q`?q`?q`?q`?|
000001b0  71 60 3f 5f 40 30 97 84  76 b1 99 8f a2 85 00 fe  |q`?_@0..v.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f0 4d 0b 00 fe  |............M...|
000001d0  ff ff 05 fe ff ff 02 f0  4d 0b 00 40 46 00 00 00  |........M..@F...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd

---

### Post by oldfred on 2010-11-12
I do not see anything in boot script that looks out of place. Files seem to be in correct places and boot.ini looks normal.

I would try this from XP disk

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

