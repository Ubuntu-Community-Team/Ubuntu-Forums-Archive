---
title: "LILO · GNU GRUB · SYSLINUX · LOADLIN - MBR files"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by Hakunka-Matata on 2011-03-14
============================= Boot Info Summary: ==============================
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb6 starts at sector 136130560.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Puppy Linux Linux 2.6.30.5 
                       [i686 arch]
    Boot files/dirs:   /etc/fstab

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  MEPIS Linux 8.5
    Boot files/dirs:   /etc/fstab

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2    *    102,398,310   201,680,009    99,281,700  83 Linux
/dev/sda4         201,680,010   304,078,319   102,398,310  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   136,128,511   136,128,449  83 Linux
/dev/sdb2         136,128,512   156,301,311    20,172,800   5 Extended
/dev/sdb5         152,199,810   156,296,384     4,096,575  82 Linux swap / Solaris
/dev/sdb6         136,130,560   140,226,559     4,096,000   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687  83 Linux
/dev/sdc2          40,966,144   122,879,999    81,913,856  83 Linux
/dev/sdc3         122,881,185   204,796,619    81,915,435  83 Linux
/dev/sdc4         204,796,681   488,396,799   283,600,119   5 Extended
/dev/sdc5         204,796,746   245,762,369    40,965,624  83 Linux
/dev/sdc6         245,762,433   286,728,119    40,965,687  83 Linux
/dev/sdc7         484,096,000   488,396,799     4,300,800  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5A14174B14172A11                       ntfs       WinXP                         
/dev/sda2        0fb28b1f-044f-43ff-a1b5-1b36cd43feeb   ext4       1010-separate-ho              
/dev/sda4        a9f5d94a-6571-4016-a267-1b425da6382f   ext4       sdb4_home_data                
/dev/sda: PTTYPE="dos" 
/dev/sdb1        604baae7-b8c3-4354-b042-9c8a6cb909dd   ext4       Ub-9.10                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        b83e0608-fd1f-4cc3-be87-622a0590da95   swap                                     
/dev/sdb6        BBCB-2466                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01e2ae96-7804-4da9-a8b6-52b9f62a48af   ext4       sda1_1010                     
/dev/sdc2        beba3cf3-e1e1-424c-bb79-92fe1a447734   ext4       sda2                          
/dev/sdc3        4556b6fd-c494-4200-9d85-3e4c96ea9609   ext4       Puppy 4.3.1                   
/dev/sdc4: PTTYPE="dos" 
/dev/sdc5        0c40042e-9f49-42b9-b724-974bda9c3264   ext3       sda5-Mepis                    
/dev/sdc6        7337c5df-44c6-4ee5-b72d-6fd187db55f7   ext4       sda6                          
/dev/sdc7        339ad7c0-32c0-489d-a013-3c36d2181d73   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc2        /media/sdc2              ext4       (rw,errors=remount-ro)
/dev/sdc3        /media/sdc3_Puppy        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
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
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5a14174b14172a11
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sdb1 ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sdb1 ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdc1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdc1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sdc1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sdc1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdc1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sdc1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos3)'
	search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
	linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos3)'
	search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
	linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sdc5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set 0c40042e-9f49-42b9-b724-974bda9c3264
	linux /boot/vmlinuz-2.6.32-1-mepis64-smp root=/dev/sdc5
	initrd /boot/initrd.img-2.6.32-1-mepis64-smp
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b83e0608-fd1f-4cc3-be87-622a0590da95 none            swap    sw              0       0
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=a9f5d94a-6571-4016-a267-1b425da6382f   /home    ext4          nodev,nosuid       0       2 
# FAT32 lba,BOOT /dev/sda8 Mint extracted iso install disc
UUID=BBCB-2466 				/FAT32sda7	vfat	umask=0000,utf8   	0       0

=================== sda2: Location of files loaded by Grub: ===================


  86.9GB: boot/grub/core.img
  65.9GB: boot/grub/grub.cfg
  75.3GB: boot/initrd.img-2.6.35-22-generic
  54.7GB: boot/initrd.img-2.6.35-23-generic
  75.3GB: boot/initrd.img-2.6.35-24-generic
  54.4GB: boot/initrd.img-2.6.35-25-generic
  55.3GB: boot/initrd.img-2.6.35-27-generic
  87.0GB: boot/vmlinuz-2.6.35-22-generic
  87.0GB: boot/vmlinuz-2.6.35-23-generic
  87.1GB: boot/vmlinuz-2.6.35-24-generic
  87.1GB: boot/vmlinuz-2.6.35-25-generic
  87.1GB: boot/vmlinuz-2.6.35-27-generic
  55.3GB: initrd.img
  54.4GB: initrd.img.old
  87.1GB: vmlinuz
  87.1GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 5a14174b14172a11
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
	insmod ext2
	set root=(hd2,3)
	search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
	linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
	insmod ext2
	set root=(hd2,3)
	search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
	linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sdc5)" {
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set 0c40042e-9f49-42b9-b724-974bda9c3264
	linux /boot/vmlinuz-2.6.32-1-mepis64-smp root=/dev/sdc5
	initrd /boot/initrd.img-2.6.32-1-mepis64-smp
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
UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b83e0608-fd1f-4cc3-be87-622a0590da95 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  56.3GB: boot/grub/core.img
  56.3GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
  32.2GB: boot/initrd.img-2.6.31-22-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
  27.2GB: boot/vmlinuz-2.6.31-22-generic
  32.2GB: initrd.img
    .5GB: initrd.img.old
  27.2GB: vmlinuz
    .5GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdb6: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg

=========================== sdc1/boot/grub/menu.lst: ===========================

sudo nano /boot/grub/menu.lst

that's how this file was created, just testing

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5a14174b14172a11
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
	insmod ext2
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
	linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
	insmod ext2
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
	linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sdc5)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set 0c40042e-9f49-42b9-b724-974bda9c3264
	linux /boot/vmlinuz-2.6.32-1-mepis64-smp root=/dev/sdc5
	initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> 				<mount point>   <type>  <options>       	<dump>  <pass>
proc            				/proc           proc    nodev,noexec,nosuid 	0       0
# / was on /dev/sdc1 during installation
UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af 	/               ext4    errors=remount-ro 	0       1
# / was on /dev/sdc2 during installation
UUID=beba3cf3-e1e1-424c-bb79-92fe1a447734 	/media/sdc2     ext4    errors=remount-ro 	0       1
# / was on /dev/sdc3 Puppy 4.3.1 during installation
UUID=4556b6fd-c494-4200-9d85-3e4c96ea9609 	/media/sdc3_Puppy ext4    errors=remount-ro 	0       1
# swap was on /dev/sda5 MEPIS during installation
UUID=0c40042e-9f49-42b9-b724-974bda9c3264 	none            swap    sw             		0       0



=================== sdc1: Location of files loaded by Grub: ===================


  17.5GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
  17.4GB: boot/grub/menu.lst
  17.4GB: boot/initrd.img-2.6.32-28-generic
  17.4GB: boot/initrd.img-2.6.32-29-generic
   1.2GB: boot/initrd.img-2.6.35-22-generic
   3.4GB: boot/initrd.img-2.6.35-25-generic
  17.4GB: boot/vmlinuz-2.6.32-28-generic
  17.5GB: boot/vmlinuz-2.6.32-29-generic
  17.5GB: boot/vmlinuz-2.6.35-22-generic
  17.6GB: boot/vmlinuz-2.6.35-25-generic
   3.4GB: initrd.img
   1.2GB: initrd.img.old
  17.6GB: vmlinuz
  17.5GB: vmlinuz.old

=============================== sdc3/etc/fstab: ===============================

/dev/sdb3     /            ext4     defaults               0 1
none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0

=================== sdc3: Location of files loaded by Grub: ===================


  63.2GB: boot/vmlinuz

=============================== sdc5/etc/fstab: ===============================

# Pluggable devices are handled by uDev, they are not in fstab
/dev/sda6 / ext3 defaults,noatime 1 1
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
# Dynamic entries below
/dev/sda1 /mnt/sda1 ntfs-3g noauto,users,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/sda2 /mnt/sda2 ext4 noauto,users,exec,relatime 0 0
/dev/sda4 /mnt/sda4 ext4 noauto,users,exec,relatime 0 0
/dev/sdb1 /mnt/sdb1 ext4 noauto,users,exec,relatime 0 0
/dev/sdb5 swap swap sw,pri=1 0 0
/dev/sdb6 /mnt/sdb6 vfat noauto,users,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/sdc1 /mnt/sdc1 ext4 noauto,users,exec,relatime 0 0
/dev/sdc2 /mnt/sdc2 ext4 noauto,users,exec,relatime 0 0
/dev/sdc3 /mnt/sdc3 ext4 noauto,users,exec,relatime 0 0
/dev/sdc5 /mnt/sdc5 ext3 noauto,users,exec,relatime 0 0
/dev/sdc6 /mnt/sdc6 ext4 noauto,users,exec,relatime 0 0
/dev/sdc7 swap swap sw,pri=1 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/sr1 /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/cdrom1 /media/cdrom1 udf,iso9660 noauto,users,exec,ro 0 0
/dev/sr0 /media/cdrom1 udf,iso9660 noauto,users,exec,ro 0 0

=================== sdc5: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/stage2
 111.8GB: boot/initrd.img
 111.8GB: boot/initrd.img-2.6.32-1-mepis64-smp
 111.8GB: boot/vmlinuz
 111.8GB: boot/vmlinuz-2.6.32-1-mepis64-smp
```

After many experiments creating install (LiveCDs) on partitions in my harddrives, and then booting to those partitions to install new OSes, RESULTS.txt shows some inconsistencies, how to clean them up? 

```

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for [COLOR="Magenta"](,msdos2)[/COLOR]/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

```

[COLOR="Magenta"](,msdos2)[/COLOR] part of sda MBR only??

```
sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   [COLOR="Magenta"]/boot/grub/menu.lst[/COLOR] /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

```
[COLOR="Magenta"]/boot/grub/menu.lst[/COLOR] hanging around from SYSLINUX install (I think) at one time, how do I get rid of it?

I've done most of the Grub 'purge, reconfigure, update xyz, procedures' from oldfred and drs305's guides and that got the non-booting drives working right again, but still have these inconsistencies.  Machine boots, from all drives, into all OS choices, but I'd like to understand how to clean up the inconsistencies completely.

Thanks in advance for guidance

---

