---
title: "upgrade-grub can not find my other linux OS"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by misko_ on 2010-12-28
Hello,

Yesterday I did "apt-get update && apt-get upgrade" of my CrunchBang Linux distribution(which is now based on debian, previously it was on ubuntu, and in my opinion than it was better).
I think that it did grub update, and after that I was having following error: "error: the symbol 'grub_xputs' not found"
I was goggling and I found:
[http://ubuntuforums.org/showthread.php?t=1580752](http://ubuntuforums.org/showthread.php?t=1580752)
[http://ubuntuforums.org/showpost.php?p=9836539&postcount=5](http://ubuntuforums.org/showpost.php?p=9836539&postcount=5)
I followed its instruction bit id did not help me.

After that I decided to install Ubutnu 10.10 in hope that it will recognise my CrunchBang installation, and make it available in grub menu when booting.
Unfortunately that did not happen.
I hope that somebody can me explain why it did not happen, and how to solve it.

this is my fdisk -l
```

sasa@sasa-System-Name:~/Downloads$ sudo fdisk -l
[sudo] password for sasa: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x264e264d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  82  Linux swap / Solaris
/dev/sda3             245        4195    31736407+   7  HPFS/NTFS
/dev/sda4            4196       14278    80985089    5  Extended
/dev/sda5            8403       10361    15729664   83  Linux
/dev/sda6           10361       12319    15729664   83  Linux
/dev/sda7           12320       14278    15729664   83  Linux
/dev/sda8            4196        8403    33793024   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x61ef507f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 131 MB, 131072000 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df525

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          15      120456    6  FAT16

Disk /dev/sdd: 4060 MB, 4060086272 bytes
255 heads, 63 sectors/track, 493 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x434f4475

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         493     3959991    b  W95 FAT32


```

This is output from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 149008384 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  CrunchBang Linux statler
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     1,959,929     1,959,867  82 Linux swap / Solaris
/dev/sda3           3,919,860    67,392,674    63,472,815   7 HPFS/NTFS
/dev/sda4          67,395,582   229,365,759   161,970,178   5 Extended
/dev/sda5         134,983,680   166,443,007    31,459,328  83 Linux
/dev/sda6         166,445,056   197,904,383    31,459,328  83 Linux
/dev/sda7         197,906,432   229,365,759    31,459,328  83 Linux
/dev/sda8          67,395,584   134,981,631    67,586,048  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 131 MB, 131072000 bytes
255 heads, 63 sectors/track, 15 cylinders, total 256000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63       240,974       240,912   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        871b4bf1-fd3b-4f61-b822-bd2e50b0eb78   swap                                     
/dev/sda3        5894A87894A85A70                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        13391b1f-66a3-415f-a57d-4e7d36154d78   ext3                                     
/dev/sda6        1a9b170c-f556-4dc8-8a17-068eb2178ca4   ext3                                     
/dev/sda7        261b569a-9636-48e5-b23a-376b66d6311f   ext4                                     
/dev/sda8        c604bdf4-a9cf-42a9-960b-4f1a854ac50c   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        de2cd250-c96d-4af6-8f1a-3d96fb9120e9   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        479E-4211                              vfat       USB_128M                      
/dev/sdc         479E-3F94                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/USB_128M          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda3/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 13391b1f-66a3-415f-a57d-4e7d36154d78
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 13391b1f-66a3-415f-a57d-4e7d36154d78
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 13391b1f-66a3-415f-a57d-4e7d36154d78
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png ; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 5894a87894a85a70
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "CruncBanh Linux" {
set root=(hd0,5) 
linux /vmlinuz
initrd /initrd.img
}      
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/hda5 during installation
UUID=13391b1f-66a3-415f-a57d-4e7d36154d78 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/hda2 during installation
UUID=054dc8b8-2df2-4c93-9fd9-198e6ed3b283 /boot           ext2    defaults        0       2
# /home was on /dev/hda8 during installation
UUID=c604bdf4-a9cf-42a9-960b-4f1a854ac50c /home           ext3    defaults        0       2
# swap was on /dev/hda1 during installation
UUID=871b4bf1-fd3b-4f61-b822-bd2e50b0eb78 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#HOME
/dev/sdb1      /home/sasa/03_BIG_HDD      ext3 defaults 1 2

=================== sda5: Location of files loaded by Grub: ===================


  76.3GB: boot/grub/core.img
  76.2GB: boot/grub/grub.cfg

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 261b569a-9636-48e5-b23a-376b66d6311f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 261b569a-9636-48e5-b23a-376b66d6311f
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 261b569a-9636-48e5-b23a-376b66d6311f
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=261b569a-9636-48e5-b23a-376b66d6311f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 261b569a-9636-48e5-b23a-376b66d6311f
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=261b569a-9636-48e5-b23a-376b66d6311f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 261b569a-9636-48e5-b23a-376b66d6311f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=261b569a-9636-48e5-b23a-376b66d6311f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 261b569a-9636-48e5-b23a-376b66d6311f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=261b569a-9636-48e5-b23a-376b66d6311f ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 261b569a-9636-48e5-b23a-376b66d6311f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 261b569a-9636-48e5-b23a-376b66d6311f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 5894a87894a85a70
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=871b4bf1-fd3b-4f61-b822-bd2e50b0eb78 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 108.3GB: boot/grub/core.img
 114.7GB: boot/grub/grub.cfg
 102.8GB: boot/initrd.img-2.6.35-22-generic
 102.9GB: boot/initrd.img-2.6.35-24-generic
 108.3GB: boot/vmlinuz-2.6.35-22-generic
 108.1GB: boot/vmlinuz-2.6.35-24-generic
 102.9GB: initrd.img
 102.8GB: initrd.img.old
 108.1GB: vmlinuz
 108.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 3c 90 00 6b 64 6f 73  66 73 00 00 02 04 01 00  |.<..kdosfs......|
00000010  02 00 02 00 00 f8 fa 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 e8 03 00 00 00 29 94  3f 9e 47 20 20 20 20 20  |......).?.G     |
00000030  20 20 20 20 20 20 00 41  54 31 36 20 20 20 0e 1f  |      .AT16   ..|
00000040  be 5b 7c ac 22 c0 74 0b  56 b4 0e bb 07 00 cd 10  |.[|.".t.V.......|
00000050  5e eb f0 32 e4 cd 16 cd  19 eb fe 54 68 69 73 20  |^..2.......This |
00000060  69 73 20 6e 6f 74 20 61  20 62 6f 6f 74 61 62 6c  |is not a bootabl|
00000070  65 20 64 69 73 6b 2e 20  20 50 6c 65 61 73 65 20  |e disk.  Please |
00000080  69 6e 73 65 72 74 20 61  20 62 6f 6f 74 61 62 6c  |insert a bootabl|
00000090  65 20 66 6c 6f 70 70 79  20 61 6e 64 0d 0a 70 72  |e floppy and..pr|
000000a0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 74  |ess any key to t|
000000b0  72 79 20 61 67 61 69 6e  20 2e 2e 2e 20 0d 0a 00  |ry again ... ...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  25 f5 0d 00 00 00 80 01  |........%.......|
000001c0  01 00 06 fe 3f 0e 3f 00  00 00 10 ad 03 00 00 00  |....?.?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

So how can I make it that I have /dev/sda5 in grub boot menu ?
Previously I had /dev/sda5 for my boot partition when I used CrunchBang ?
Now I have deleted /dev/sda5.

Can anybody helm me ?

---

### Post by Quackers on 2010-12-28
It looks like you haven't run sudo update-grub since you installed 10.10 Would that be correct?
Your etc/fstab refers to hda1, hda2 and hda8, rather than sda's. Presumably because the fstab being used is from sda5 (Crunchbang).
That is what makes me say the sudo update-grub hasn't been run.
I also assume that Windows doesn't boot. This is probably because the boot flag is on sda1, which is now a swap partition. The boot flag should be on sda3 - use gparted to fix that.

---

### Post by misko_ on 2010-12-28
I HAVE FOUND THE PROBLEM.

Problem was the following:
1. Previously I had separate /boot partition and my initrd.img and vmlinuz was on that partition.
so update-grub did not make any entries in menu because he did not know how to do it.

All what I need to do now is to found last valid initrd.img and vmlinuz for my CrunchBang and I hope it should be fine.

---

