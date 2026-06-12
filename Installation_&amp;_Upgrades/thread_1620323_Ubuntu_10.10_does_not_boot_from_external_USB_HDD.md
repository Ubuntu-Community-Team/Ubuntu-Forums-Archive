---
title: "Ubuntu 10.10 does not boot from external USB HDD"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by cacoon on 2010-11-12
I Installed Ubuntu 10.10 on an external USB Disk Drive - I had chosen to install the boot loader on this drive. When I tried to boot from this drive, I get the the following message:

error: unknown filesystem

after that I get  "grub rescue>" prompt

The install was done on /dev/sdb2

I have also tried  update-grub using ubuntu 10.04 that i have on my internal drive.  It did recognize that I had a kernel on the external drive but still no luck booting. This time i get.

error: no such device d4a3cb16-37b6-416c-a3bc-4f8d03318e28
error: unknown file system
error: you need to load the kernel first

Note that the long device name is the same as the mount point when i do a "df"

---

### Post by garvinrick4 on 2010-11-12
Go to this web site and download the script to DESKTOP and then run the code below in a terminal and it will put a file named RESULTS on your desktop. Copy and paste it to your thread (after copy and paste highlight and click on the # sign in upper right of message box.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

A lot or users have the ability to read this file now and help you. 
Boot problems are not usually a difficult item to repair.

---

### Post by cacoon on 2010-11-12
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,799,999   204,593,152   7 HPFS/NTFS
/dev/sda3         204,804,094   236,052,479    31,248,386   5 Extended
/dev/sda5         204,804,096   234,098,687    29,294,592  83 Linux
/dev/sda6         234,100,736   236,052,479     1,951,744  82 Linux swap / Solaris
/dev/sda4         236,052,480   312,578,047    76,525,568   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   737,287,109   737,287,047   7 HPFS/NTFS
/dev/sdb2    *    737,288,192   854,474,751   117,186,560  83 Linux
/dev/sdb3         854,476,798   858,380,287     3,903,490   5 Extended
/dev/sdb5         854,476,800   858,380,287     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        029226F29226EA3D                       ntfs       System Reserved               
/dev/sda2        F23CB6F53CB6B447                       ntfs       fariddata                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        E4E2E467E2E44002                       ntfs                                     
/dev/sda5        f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397   ext4                                     
/dev/sda6        62af4661-238d-459b-9ac8-ebf3dbe41c83   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FA148B80148B3E9F                       ntfs       farid 500GB                   
/dev/sdb2        d4a3cb16-37b6-4168-a885-a6cdbfb4bea4   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        c278ab48-7519-4154-bdee-287de4131093   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb2        /media/d4a3cb16-37b6-4168-a885-a6cdbfb4bea4 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/farid 500GB       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 029226f29226ea3d
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set d4a3cb16-37b6-4168-a885-a6cdbfb4bea4
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d4a3cb16-37b6-4168-a885-a6cdbfb4bea4 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set d4a3cb16-37b6-4168-a885-a6cdbfb4bea4
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d4a3cb16-37b6-4168-a885-a6cdbfb4bea4 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 43a7887e-a6c2-4ebc-a3bc-4f8d03318e28
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=43a7887e-a6c2-4ebc-a3bc-4f8d03318e28 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 43a7887e-a6c2-4ebc-a3bc-4f8d03318e28
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=43a7887e-a6c2-4ebc-a3bc-4f8d03318e28 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=62af4661-238d-459b-9ac8-ebf3dbe41c83 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 113.5GB: boot/grub/core.img
 108.9GB: boot/grub/grub.cfg
 116.6GB: boot/initrd.img-2.6.32-23-generic
 115.4GB: boot/initrd.img-2.6.32-24-generic
 116.7GB: boot/initrd.img-2.6.32-25-generic
 116.6GB: boot/vmlinuz-2.6.32-23-generic
 115.2GB: boot/vmlinuz-2.6.32-24-generic
 116.6GB: boot/vmlinuz-2.6.32-25-generic
 116.7GB: initrd.img
 115.4GB: initrd.img.old
 116.6GB: vmlinuz
 115.2GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set d4a3cb16-37b6-4168-a885-a6cdbfb4bea4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set d4a3cb16-37b6-4168-a885-a6cdbfb4bea4
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set d4a3cb16-37b6-4168-a885-a6cdbfb4bea4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d4a3cb16-37b6-4168-a885-a6cdbfb4bea4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set d4a3cb16-37b6-4168-a885-a6cdbfb4bea4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d4a3cb16-37b6-4168-a885-a6cdbfb4bea4 ro single 
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
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set d4a3cb16-37b6-4168-a885-a6cdbfb4bea4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set d4a3cb16-37b6-4168-a885-a6cdbfb4bea4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 029226f29226ea3d
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=f31f8aa6-5d0d-4d7f-bc0a-71b9a27e3397 ro single
	initrd /boot/initrd.img-2.6.32-23-generic
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=d4a3cb16-37b6-4168-a885-a6cdbfb4bea4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=62af4661-238d-459b-9ac8-ebf3dbe41c83 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=c278ab48-7519-4154-bdee-287de4131093 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 379.7GB: boot/grub/core.img
 407.7GB: boot/grub/grub.cfg
 378.3GB: boot/initrd.img-2.6.35-22-generic
 379.7GB: boot/vmlinuz-2.6.35-22-generic
 378.3GB: initrd.img
 379.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  10 63 27 3c 56 c5 4b c5  64 73 bc b1 56 bf b9 d9  |.c'<V.K.ds..V...|
00000010  10 98 71 67 9a c6 d6 47  65 a2 0c 88 63 10 40 01  |..qg...Ge...c.@.|
00000020  69 0a bc 02 b3 0b 46 73  80 6d a3 e5 7a e4 a4 33  |i.....Fs.m..z..3|
00000030  43 89 df b0 a1 43 91 9d  c2 b2 1e 5d b6 aa 3d f6  |C....C.....]..=.|
00000040  fd 2b ec de 96 5a 51 3f  ff ff fe 80 cc 0c 73 37  |.+...ZQ?......s7|
00000050  54 e0 09 30 42 90 a9 7a  b5 75 15 52 f6 25 1b 6b  |T..0B..z.u.R.%.k|
00000060  a9 82 ca 91 d4 78 2c 92  1d 7f 61 e8 00 28 05 82  |.....x,...a..(..|
00000070  46 8c 9a 50 2c f2 60 30  9b bc 2d 46 88 56 23 62  |F..P,.`0..-F.V#b|
00000080  96 86 39 39 b3 d1 a4 b0  49 09 84 62 90 58 2f 62  |..99....I..b.X/b|
00000090  eb a6 e6 c7 5a b2 55 11  68 a4 ef 3a 71 1b d9 e7  |....Z.U.h..:q...|
000000a0  51 36 62 49 cd 25 15 3a  90 fc 23 26 90 49 32 a9  |Q6bI.%.:..#&.I2.|
000000b0  b1 7d 26 cd d6 ba f2 4a  e4 a4 ed 10 d9 60 a8 24  |.}&....J.....`.$|
000000c0  40 54 73 84 c7 d6 71 df  d9 e9 47 70 51 17 e2 2f  |@Ts...q...GpQ../|
000000d0  26 6b 0a 6d 1a 90 18 29  1e e2 61 f4 80 1e b6 f1  |&k.m...)..a.....|
000000e0  54 69 8f 92 c3 0e b9 b0  32 1e 38 b0 54 f9 67 ba  |Ti......2.8.T.g.|
000000f0  f8 8a 32 74 f3 18 ef ff  91 00 01 f3 1b 33 95 03  |..2t.........3..|
00000100  54 a2 30 9a b2 cc 87 9f  47 61 da 60 d1 14 56 8c  |T.0.....Ga.`..V.|
00000110  00 86 6d 65 b2 e1 30 30  64 62 8e 21 00 00 00 00  |..me..00db.!....|
00000120  01 b6 57 b8 fc 06 6c 3b  c5 d1 c7 2a c6 6f 16 af  |..W...l;...*.o..|
00000130  59 a7 b5 bd ad e4 da e9  13 d8 de a6 f7 8d f7 bd  |Y...............|
00000140  ea 6f 78 b4 9e 25 36 f0  cd e2 08 93 de f1 15 b7  |.ox..%6.........|
00000150  bc fb c4 db de 21 53 de  f7 85 a5 7b dc 16 4c df  |.....!S....{..L.|
00000160  4f bd c2 97 3b 4f 80 58  a1 5c 19 8a 52 7d 3e 01  |O...;O.X.\..R}>.|
00000170  62 b6 13 4f 83 3c 2d 10  53 c0 2d c1 88 0b 59 ce  |b..O.<-.S.-...Y.|
00000180  63 e4 87 17 77 97 d0 e7  df fc 0a 7f cf e8 fe c1  |c...w...........|
00000190  10 67 ae f1 e7 c3 c1 4d  fc 0d a0 a8 19 d5 45 fb  |.g.....M......E.|
000001a0  7b 2b 8b 8d c8 eb af 70  53 b2 fd 3e 25 eb ef 55  |{+.....pS..>%..U|
000001b0  6c 3c 5e e7 b8 06 c1 71  42 f5 6b 6f 59 43 00 fe  |l<^....qB.koYC..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 bf 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff ee 01  bf 01 14 ce 1d 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

```

---

### Post by garvinrick4 on 2010-11-13
Can someone help this user it seems he has a external as sdb that is 500 gigs
and first 400 or so is no operating system and he just installed linux on the last
100 gigs or less of sdb. It is a little sloppy looking to me but sda seems to be booting
fine with Windows and linux. This is basically a bump.

---

### Post by cacoon on 2010-11-13
Garvinkrick4 - you are right it looked pretty strange. I ended up formating the drive and installed ubuntu before i did anything else.  Works great. Thanks for the info on how to create the pretty useful report.

---

