---
title: "Ubuntu will boot, but Win XP will not"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by christhawkSMR on 2011-04-21
I had the common "10.10 killed my bootloader" problem on my older laptop (Gateway CX200S tablet), but since I rarely use it I had just put off fixing it until now.  Using the Live CD I was able to restore grub without trouble, and everything seemed normal until I tried to boot into my Windows XP partition.  Although it appears in the grub list like normal, when I choose it I get the "grub xputs not found" error like I did when grub was completely broken.  Any ideas?  Thanks!

---

### Post by wilee-nilee on 2011-04-21
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will show what is where, and most likely get us to the problems. 

Did XP run ever after the the original dual boot on this computer?

---

### Post by Rubi1200 on 2011-04-21
You should definitely follow the great advice posted by wilee-nilee and run the script so we can see what is what.

Just so you know, a grub xputs error is often caused by either missing or incorrectly configured GRUB files.

But, the boot script should help us diagnose that too.

---

### Post by christhawkSMR on 2011-04-22
Thanks guys!  Win XP has booted before - I've had this as a dual-boot machine since 8.10, I think.  It has dual-booted successfully for me with every previous distro.  

Here's the boot info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 122449187 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   116,374,859   116,374,797   7 HPFS/NTFS
/dev/sda2         116,374,860   156,296,384    39,921,525   5 Extended
/dev/sda5         116,374,923   154,545,299    38,170,377  83 Linux
/dev/sda6         154,545,363   156,296,384     1,751,022  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56DC536684924782                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        62ae7607-6504-4848-b5f3-82957ccdd7fe   ext4                                     
/dev/sda6        90847255-ab82-4c2f-ab01-638d823a9999   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 56dc536684924782
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=90847255-ab82-4c2f-ab01-638d823a9999 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  68.7GB: boot/grub/core.img
  60.7GB: boot/grub/grub.cfg
  68.8GB: boot/initrd.img-2.6.31-19-generic
  71.8GB: boot/initrd.img-2.6.32-25-generic
  73.2GB: boot/initrd.img-2.6.35-22-generic
  73.7GB: boot/initrd.img-2.6.35-28-generic
  60.8GB: boot/vmlinuz-2.6.31-19-generic
  69.0GB: boot/vmlinuz-2.6.32-25-generic
  71.8GB: boot/vmlinuz-2.6.35-22-generic
  67.3GB: boot/vmlinuz-2.6.35-28-generic
  73.7GB: initrd.img
  73.2GB: initrd.img.old
  67.3GB: vmlinuz
  71.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Rubi1200 on 2011-04-22
It seems that GRUB was somehow installed to the Windows boot sector on sda1.

First step is to fix the Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Then, when Windows is booting normally, reinstall GRUB making sure it is to the MBR of sda:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by christhawkSMR on 2011-04-22
Hmm... Now I seem to have broken it completely.  Running fixboot and fixmbr from the Windows XP disk seemed to work (it came up as successful); however, grub still came up and XP would not load.  I tried reinstalling grub.  Now when I start up I get the following:
```
GNU GRUB version 1.98+20100804-5ubuntu3

Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device or file completions.
```

and a grub> prompt.  Where do I go from here?

---

### Post by Rubi1200 on 2011-04-23
Please run the boot info script again and post the results so we can see what has changed.

Thanks.

---

### Post by christhawkSMR on 2011-04-25
Here you go - I should have thought to do that before, huh?  Newest boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 122449187 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   116,374,859   116,374,797   7 HPFS/NTFS
/dev/sda2         116,374,860   156,296,384    39,921,525   5 Extended
/dev/sda5         116,374,923   154,545,299    38,170,377  83 Linux
/dev/sda6         154,545,363   156,296,384     1,751,022  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        56DC536684924782                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        62ae7607-6504-4848-b5f3-82957ccdd7fe   ext4                                     
/dev/sda6        90847255-ab82-4c2f-ab01-638d823a9999   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/62ae7607-6504-4848-b5f3-82957ccdd7fe ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    echo    'Loading Linux 2.6.31-19-generic ...'
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56dc536684924782
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=90847255-ab82-4c2f-ab01-638d823a9999 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  68.6GB: boot/grub/core.img
  61.0GB: boot/grub/grub.cfg
  68.8GB: boot/initrd.img-2.6.31-19-generic
  71.8GB: boot/initrd.img-2.6.32-25-generic
  73.2GB: boot/initrd.img-2.6.35-22-generic
  73.7GB: boot/initrd.img-2.6.35-28-generic
  60.8GB: boot/vmlinuz-2.6.31-19-generic
  69.0GB: boot/vmlinuz-2.6.32-25-generic
  71.8GB: boot/vmlinuz-2.6.35-22-generic
  67.3GB: boot/vmlinuz-2.6.35-28-generic
  73.7GB: initrd.img
  73.2GB: initrd.img.old
  67.3GB: vmlinuz
  71.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by wilee-nilee on 2011-04-25
> **christhawkSMR said:**
> Hmm... Now I seem to have broken it completely.  Running fixboot and fixmbr from the Windows XP disk seemed to work (it came up as successful); however, grub still came up and XP would not load.  I tried reinstalling grub.  Now when I start up I get the following:
```
GNU GRUB version 1.98+20100804-5ubuntu3

Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device or file completions.
```

and a grub> prompt.  Where do I go from here?

Try these instructions and run the commands again you should be replacing grub in the mbr, and XP would boot, no grub menu would be seen if done correctly. We need to fix XP and running the script will tell **you** if the grub has been removed from the sda1 partition.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Are you seeing this at the XP command line? 
C:\Windows>
If not then run the letter of your drive X: /fixmbr 
then /fixboot
X=drive letter

To be honest some of the forum tutorials although effective can be a bit confusing to some of us.

---

### Post by christhawkSMR on 2011-04-25
> **wilee-nilee said:**
> 
Are you seeing this at the XP command line? 
C:\Windows>

No.  When I run the "R"ecover/restore prompt from the XP disk, it takes me to a prompt of C:\.  It will not let me cd into C:\Windows, either.  It gives me a "there is no floppy disk or CD in the drive" error, strangely.

> **wilee-nilee said:**
> 
If not then run the letter of your drive X: /fixmbr 
then /fixboot
X=drive letter

Still did not rewrite.  Fixboot said the sector was corrupt and gave me a successful rewrite message, but fixmbr did not appear to do anything at all.

---

### Post by wilee-nilee on 2011-04-25
> **christhawkSMR said:**
> No.  When I run the "R"ecover/restore prompt from the XP disk, it takes me to a prompt of C:\.  It will not let me cd into C:\Windows, either.  It gives me a "there is no floppy disk or CD in the drive" error, strangely.



Still did not rewrite.  Fixboot said the sector was corrupt and gave me a successful rewrite message, but fixmbr did not appear to do anything at all.

I let another member know of your situation, and they are on daily so hang on bro/sis, we are trying to get you up and running.
;)

---

### Post by oldfred on 2011-04-25
This is the problem:

sda1: _________________

    File system:       ntfs
    [COLOR=Red]Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 122449187 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Windows has to have its boot code in the partition boot sector (PBR).

This usually works. From your install or a liveCD.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

hopefully rerunning the fixboot did not create a corrupt backup also.

---

### Post by christhawkSMR on 2011-04-25
Okay, so it seems to have fixed the Windows error!  But, grub still gives me the strange prompt instead of the boot list.  I tried to reinstall but I could not mount the sda5 partition (where Ubuntu is).  Here's the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   116,374,859   116,374,797   7 HPFS/NTFS
/dev/sda2         116,374,860   156,296,384    39,921,525   5 Extended
/dev/sda5         116,374,923   154,545,299    38,170,377  83 Linux
/dev/sda6         154,545,363   156,296,384     1,751,022  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        56DC536684924782                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        62ae7607-6504-4848-b5f3-82957ccdd7fe   ext4                                     
/dev/sda6        90847255-ab82-4c2f-ab01-638d823a9999   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/56DC536684924782  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/62ae7607-6504-4848-b5f3-82957ccdd7fe ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    echo    'Loading Linux 2.6.31-19-generic ...'
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 62ae7607-6504-4848-b5f3-82957ccdd7fe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56dc536684924782
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=62ae7607-6504-4848-b5f3-82957ccdd7fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=90847255-ab82-4c2f-ab01-638d823a9999 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  68.6GB: boot/grub/core.img
  61.0GB: boot/grub/grub.cfg
  68.8GB: boot/initrd.img-2.6.31-19-generic
  71.8GB: boot/initrd.img-2.6.32-25-generic
  73.2GB: boot/initrd.img-2.6.35-22-generic
  73.7GB: boot/initrd.img-2.6.35-28-generic
  60.8GB: boot/vmlinuz-2.6.31-19-generic
  69.0GB: boot/vmlinuz-2.6.32-25-generic
  71.8GB: boot/vmlinuz-2.6.35-22-generic
  67.3GB: boot/vmlinuz-2.6.35-28-generic
  73.7GB: initrd.img
  73.2GB: initrd.img.old
  67.3GB: vmlinuz
  71.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by oldfred on 2011-04-25
Script looks ok. Are you getting grub> prompt or system rescue?

You can try manually booting. If that does not work and the short two line reinstall does not work then the full chroot version to to reinstall grub is worth trying.

Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

or
Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,5) or sda5
sh:grub>ls (hd0,5)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,5)/vmlinuz root=/dev/sda5
sh:grub>initrd (hd0,5)/initrd.img
sh:grub>boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by christhawkSMR on 2011-04-27
Finally!  It worked!  I was able to manually boot, and the chroot reinstall finally did the trick to get grub back to normal, now that the Win XP loader was back to working.  Thank you all so much!

---

