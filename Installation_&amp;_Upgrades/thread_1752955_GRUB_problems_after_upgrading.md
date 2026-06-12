---
title: "GRUB problems after upgrading"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by Mauricio_A on 2011-05-08
So, basically after upgrading to 11.04 and doing a million things my system works but GRUB is being a roulette. I'll try to make this as short as possible:

Initially I had 6 partitions in 2 hard drives:
In the first drive two NTFS partitions (sda1 and sda2, with labels F and C), one with only files and the other one with a non-free operative system installed (that I rarely used, but still worked).

In the second drive I had 4 partitions: The first one (sdb1, labelled Archivos) was a big NTFS partitions with files only that I used all the time with Ubuntu (this is where I saved most of my files).
Then I had 2 ext4 partitions (sdb4 and sdb2). sdb4 had Ubuntu 10.10, which I used every day. sdb2 was from an older Ubuntu installation that wasn't working anymore, and I'm not sure why I kept it.
Finally sbd3 was an extended partition with the swap area.

So, I decided to upgrade Ubuntu the easy way, but since I was scared of things going badly I decided to make a backup of my whole sdb4 partition with Ubuntu inside. For this I shrinked the sda2 NTFS partition and copied the sdb4 partition in the unallocated space using GParted live CD.

After that I rebooted Ubuntu and upgraded it to 11.04.
Something went wrong, because after the upgrade was complete Grub was all broken: the arrow keys didn't do anything and pressing enter gave me an error.
I tried everything but figured the best I could do was to reinstall grub. Since I couldn't boot to any operative system I grabbed and old Linux Mint CD that I had and tried to install grub from there, but I didn't know how to, so I had no choice but to install Mint in the sdb2 partition (the old Ubuntu partition that didn't work and I wasn't using anymore), and hope for it to install GRUB after finishing installing Mint. 

So, now Grub works again, and I can boot to Mint (which I plan on deleting once this is fixed) or Ubuntu 11.04 or Ubuntu 10.10.
The problem is, if I try to boot to Ubuntu there's a 50% chance it will boot to 10.10 and a 50% chance it will boot to 11.04. There are a million options to boot from (different kernels?), but even if I always select the same it's completely random.

So basically, how can I fix this? Both 10.10 and 11.04 are working, but I can't choose where to boot...
If I need to post more information about my partitions just tell me.
Sorry for being too long and sorry for my bad English.

---

### Post by Hedgehog1 on 2011-05-08
Please boot into one of your Ubuntu installs, and then do this:


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.


***The Hedge***

:KS

---

### Post by Mauricio_A on 2011-05-08
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   167,798,924   167,798,862   7 HPFS/NTFS
/dev/sda2    *    167,798,928   276,925,120   109,126,193   7 HPFS/NTFS
/dev/sda3         276,926,464   312,580,095    35,653,632  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,884,028,227 1,884,028,165   7 HPFS/NTFS
/dev/sdb2       1,917,582,660 1,950,612,299    33,029,640  83 Linux
/dev/sdb3       1,950,612,361 1,953,520,064     2,907,704   5 Extended
/dev/sdb5       1,950,612,363 1,953,520,064     2,907,702  82 Linux swap / Solaris
/dev/sdb4    *  1,884,028,928 1,917,581,311    33,552,384  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5F0AADA934058B60                       ntfs       F                             
/dev/sda2        686ADC9E6ADC6A78                       ntfs       C                             
/dev/sda3        88513ffd-bfcf-4235-a8cc-0de32282ecad   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        062E615E2E6147AF                       ntfs       Archivos                      
/dev/sdb2        ba217d41-c214-4595-8265-e5884dea3f81   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        88513ffd-bfcf-4235-a8cc-0de32282ecad   ext4                                     
/dev/sdb5        25a3efad-a268-4380-923f-257a39ec14fc   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Archivos          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/C                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/F                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/ba217d41-c214-4595-8265-e5884dea3f81 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(3)\windows
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\windows="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

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
search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5f0aada934058b60
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 686adc9e6adc6a78
	chainloader +1
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2) (on /dev/sdb2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2) -- recovery mode (on /dev/sdb2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb4 :
UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=062E615E2E6147AF	/media/Archivos	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=686ADC9E6ADC6A78	/media/C	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=5F0AADA934058B60	/media/F	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=25a3efad-a268-4380-923f-257a39ec14fc	none	swap	sw	0	0



=================== sda3: Location of files loaded by Grub: ===================


 152.7GB: boot/grub/core.img
 155.9GB: boot/grub/grub.cfg
 158.6GB: boot/initrd.img-2.6.32-25-generic
 156.0GB: boot/initrd.img-2.6.35-22-generic
 158.6GB: boot/initrd.img-2.6.35-23-generic
 150.2GB: boot/initrd.img-2.6.35-24-generic
 141.8GB: boot/initrd.img-2.6.35-25-generic
 148.0GB: boot/initrd.img-2.6.35-27-generic
 150.0GB: boot/initrd.img-2.6.35-28-generic
 153.0GB: boot/vmlinuz-2.6.32-25-generic
 153.1GB: boot/vmlinuz-2.6.35-22-generic
 156.1GB: boot/vmlinuz-2.6.35-23-generic
 156.0GB: boot/vmlinuz-2.6.35-24-generic
 158.8GB: boot/vmlinuz-2.6.35-25-generic
 146.1GB: boot/vmlinuz-2.6.35-27-generic
 153.3GB: boot/vmlinuz-2.6.35-28-generic
 150.0GB: initrd.img
 148.0GB: initrd.img.old
 153.3GB: vmlinuz
 146.1GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
set locale_dir=($root)/boot/grub/locale
set lang=es
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5f0aada934058b60
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 686adc9e6adc6a78
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, con Linux 2.6.38-8-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, con Linux 2.6.38-8-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, con Linux 2.6.35-28-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, con Linux 2.6.35-28-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, con Linux 2.6.32-25-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, con Linux 2.6.32-25-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=ba217d41-c214-4595-8265-e5884dea3f81 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=25a3efad-a268-4380-923f-257a39ec14fc none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 986.2GB: boot/grub/core.img
 993.2GB: boot/grub/grub.cfg
 986.2GB: boot/initrd.img-2.6.32-21-generic
 986.2GB: boot/vmlinuz-2.6.32-21-generic
 986.2GB: initrd.img
 986.2GB: vmlinuz

=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
set locale_dir=($root)/boot/grub/locale
set lang=es_AR
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
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
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, con Linux 2.6.38-8-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.35-28-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 5F0AADA934058B60
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 686ADC9E6ADC6A78
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro ipv6.disable=1 quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro single ipv6.disable=1
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro ipv6.disable=1 quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro single ipv6.disable=1
	initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb4 :
UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=062E615E2E6147AF	/media/Archivos	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=686ADC9E6ADC6A78	/media/C	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=5F0AADA934058B60	/media/F	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=25a3efad-a268-4380-923f-257a39ec14fc	none	swap	sw	0	0



=================== sdb4: Location of files loaded by Grub: ===================


 975.5GB: boot/grub/core.img
 978.1GB: boot/grub/grub.cfg
 981.4GB: boot/initrd.img-2.6.32-25-generic
 972.8GB: boot/initrd.img-2.6.35-28-generic
 976.8GB: boot/initrd.img-2.6.38-8-generic
 975.8GB: boot/vmlinuz-2.6.32-25-generic
 976.1GB: boot/vmlinuz-2.6.35-28-generic
 979.1GB: boot/vmlinuz-2.6.38-8-generic
 976.8GB: initrd.img
 972.8GB: initrd.img.old
 979.1GB: vmlinuz
 976.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  87 b5 df ca 0d 94 f2 a4  a5 78 d8 09 a0 08 c0 00  |.........x......|
00000010  00 01 08 1b 7f 0f db fa  70 80 83 f8 20 83 fa e0  |........p... ...|
00000020  9b fc f4 8a 49 f2 00 18  37 f3 1d bf a6 b2 02 0f  |....I...7.......|
00000030  e0 82 0f eb d0 4c fe 90  03 92 4f 90 00 c1 bd 18  |.....L....O.....|
00000040  08 5f e3 44 12 54 90 dc  80 86 00 de 6d be 90 08  |._.D.T......m...|
00000050  60 0d 36 00 0c 8d 6f cd  c0 38 bf 40 4d 00 3f 22  |`.6...o..8.@M.?"|
00000060  43 7e 87 42 74 7b 7e 7d  a0 84 01 20 06 40 9a 00  |C~.Bt{~}... .@..|
00000070  b3 1b a0 10 c0 52 20 26  7f e9 84 86 40 87 fe e0  |.....R &....@...|
00000080  02 c6 dd 1a 18 d5 00 e1  5a c8 4d 3a b5 38 53 7c  |........Z.M:.8S||
00000090  b9 a8 a4 a6 f4 87 35 0b  0c db d5 93 75 2d aa 91  |......5.....u-..|
000000a0  2c 96 1f 4b 44 3e b7 3a  e5 fe 41 32 58 b1 24 b3  |,..KD>.:..A2X.$.|
000000b0  0d b2 55 0d c9 49 0d d0  8a 46 b2 49 b1 25 b6 c2  |..U..I...F.I.%..|
000000c0  ac b6 14 72 c6 c2 97 e9  39 b6 48 90 b4 93 64 b6  |...r....9.H...d.|
000000d0  14 7d 8a 73 73 3a 93 a9  cb 69 69 65 4b 25 85 96  |.}.ss:...iieK%..|
000000e0  b2 2a 01 4d 68 69 45 45  b4 ab 55 20 c0 da d4 3f  |.*.MhiEE..U ...?|
000000f0  1a 80 83 fd 60 07 f4 93  80 03 04 6e f6 97 1b 86  |....`......n....|
00000100  80 02 12 08 00 c3 c8 00  60 8d dc 87 c5 6c 15 69  |........`....l.i|
00000110  4d ab 67 1a ac df a5 65  18 d6 42 da c3 40 07 0d  |M.g....e..B..@..|
00000120  2a d4 2b 1f 2f 32 ad ca  ab 25 96 55 94 ea 5c b6  |*.+./2...%.U..\.|
00000130  35 d1 1f 32 49 2d 42 ad  59 12 da b0 a8 a3 5a 93  |5..2I-B.Y.....Z.|
00000140  2f 99 d2 45 4b 24 91 52  44 a5 d2 9a d7 2d b2 e5  |/..EK$.RD....-..|
00000150  96 52 ad 96 49 4a 0d a9  5b 43 4d a5 58 75 8b 93  |.R..IJ..[CM.Xu..|
00000160  4a b6 52 8b 55 b5 0e 1c  ca 29 50 b2 c2 0e 0a 92  |J.R.U....)P.....|
00000170  36 d3 52 c9 0f 2c b9 0a  89 69 74 b5 b4 e6 bd f2  |6.R..,...it.....|
00000180  5c 7c 96 ca 7d ab 65 92  42 8f 28 7b 51 96 f3 b5  |\|..}.e.B.({Q...|
00000190  56 14 7c b4 e4 89 4f 48  da 29 55 64 aa 5c b2 d2  |V.|...OH.)Ud.\..|
000001a0  45 b1 9c d3 65 92 24 a9  4b 92 d5 48 b0 b8 92 8c  |E...e.$.K..H....|
000001b0  69 42 a5 18 72 4a 52 0c  18 53 50 f4 00 4f 00 fe  |iB..rJR..SP..O..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 36 5e 2c 00 00 00  |..........6^,...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by Hedgehog1 on 2011-05-08
Thanks for posting the script output.

There are several things to fix.  Right now the grub you are running holds data in the Mint partition, so don't delete that until we get grub working from Natty.

You will need a Natty/11.04 LiveCD or LiveUSB.  If you have not already done so, please download the ISO and create a LiveCD/LiveUSB.

Once that you have built a Natty LiveCD/LiveUSB, please boot from it, select 'TRY' and then:

```
sudo mount /dev/sd**b4** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

Once this is done, you will be using grub as carried on the natty partition.

Right now you have a mish-mash of installs.  Was it your plan to keep both 10.10 and 11.04?  Or did you want to move to 11.04?

***The Hedge***

:KS

---

### Post by Mauricio_A on 2011-05-08
Thanks for the quick reply. 
I'm planning to keep 10.10 since I don't think I'll ever get used to the look of 11.04. (I'm using 10.10 right now)
Should I do what you said with a 10.10 live CD instead?

---

### Post by Hedgehog1 on 2011-05-08
Yes - if you are are keeping 10.10, make a liveCD/LiveUSB of that.

Here are the updated instructions for using 10.10's grub:

```
sudo mount /dev/sd**a3** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```


***The Hedge***

:KS

p.s. After you are booting into 10.10 correctly, you can delete the 11.0 and Mint partitions, then then do this to get them to disappear from the grub menu:

```
sudo update-grub
```

---

### Post by Mauricio_A on 2011-05-08
Thanks. I'll give it a try and report back.

---

### Post by Mauricio_A on 2011-05-08
OK, so I did that and my problem persists.

The green mint grub was replaced by the classic black grub, but choosing the default option will alternate between Ubuntu 10.10 and Ubuntu 11.04.
Right now I'm on 10.10. If I restart my computer and select the same option as before on grub, 11.04 will load. 
If I restart the computer again, 10.10 will boot.
And so on, they keep alternating. 

Maybe I have 2 grub installations and I need to uninstall one??

I don't even know which version is installed which partition (if they are even in different partitions).

Here's the output of the script, running it under 10.10:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   167,798,924   167,798,862   7 HPFS/NTFS
/dev/sda2    *    167,798,928   276,925,120   109,126,193   7 HPFS/NTFS
/dev/sda3         276,926,464   312,580,095    35,653,632  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,884,028,227 1,884,028,165   7 HPFS/NTFS
/dev/sdb2       1,917,582,660 1,950,612,299    33,029,640  83 Linux
/dev/sdb3       1,950,612,361 1,953,520,064     2,907,704   5 Extended
/dev/sdb5       1,950,612,363 1,953,520,064     2,907,702  82 Linux swap / Solaris
/dev/sdb4    *  1,884,028,928 1,917,581,311    33,552,384  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5F0AADA934058B60                       ntfs       F                             
/dev/sda2        686ADC9E6ADC6A78                       ntfs       C                             
/dev/sda3        88513ffd-bfcf-4235-a8cc-0de32282ecad   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        062E615E2E6147AF                       ntfs       Archivos                      
/dev/sdb2        ba217d41-c214-4595-8265-e5884dea3f81   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        88513ffd-bfcf-4235-a8cc-0de32282ecad   ext4                                     
/dev/sdb5        25a3efad-a268-4380-923f-257a39ec14fc   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Archivos          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/C                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/F                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(3)\windows
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\windows="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

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
search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5f0aada934058b60
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 686adc9e6adc6a78
	chainloader +1
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2) (on /dev/sdb2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2) -- recovery mode (on /dev/sdb2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb4 :
UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=062E615E2E6147AF	/media/Archivos	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=686ADC9E6ADC6A78	/media/C	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=5F0AADA934058B60	/media/F	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=25a3efad-a268-4380-923f-257a39ec14fc	none	swap	sw	0	0



=================== sda3: Location of files loaded by Grub: ===================


 152.6GB: boot/grub/core.img
 155.9GB: boot/grub/grub.cfg
 158.6GB: boot/initrd.img-2.6.32-25-generic
 156.0GB: boot/initrd.img-2.6.35-22-generic
 158.6GB: boot/initrd.img-2.6.35-23-generic
 150.2GB: boot/initrd.img-2.6.35-24-generic
 141.8GB: boot/initrd.img-2.6.35-25-generic
 148.0GB: boot/initrd.img-2.6.35-27-generic
 150.0GB: boot/initrd.img-2.6.35-28-generic
 153.0GB: boot/vmlinuz-2.6.32-25-generic
 153.1GB: boot/vmlinuz-2.6.35-22-generic
 156.1GB: boot/vmlinuz-2.6.35-23-generic
 156.0GB: boot/vmlinuz-2.6.35-24-generic
 158.8GB: boot/vmlinuz-2.6.35-25-generic
 146.1GB: boot/vmlinuz-2.6.35-27-generic
 153.3GB: boot/vmlinuz-2.6.35-28-generic
 150.0GB: initrd.img
 148.0GB: initrd.img.old
 153.3GB: vmlinuz
 146.1GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
set locale_dir=($root)/boot/grub/locale
set lang=es
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5f0aada934058b60
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 686adc9e6adc6a78
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, con Linux 2.6.38-8-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, con Linux 2.6.38-8-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, con Linux 2.6.35-28-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, con Linux 2.6.35-28-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, con Linux 2.6.32-25-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, con Linux 2.6.32-25-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=ba217d41-c214-4595-8265-e5884dea3f81 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=25a3efad-a268-4380-923f-257a39ec14fc none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 986.2GB: boot/grub/core.img
 993.2GB: boot/grub/grub.cfg
 986.2GB: boot/initrd.img-2.6.32-21-generic
 986.2GB: boot/vmlinuz-2.6.32-21-generic
 986.2GB: initrd.img
 986.2GB: vmlinuz

=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
set locale_dir=($root)/boot/grub/locale
set lang=es_AR
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
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
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, con Linux 2.6.38-8-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.35-28-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 5F0AADA934058B60
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 686ADC9E6ADC6A78
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro ipv6.disable=1 quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro single ipv6.disable=1
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro ipv6.disable=1 quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro single ipv6.disable=1
	initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb4 :
UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=062E615E2E6147AF	/media/Archivos	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=686ADC9E6ADC6A78	/media/C	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=5F0AADA934058B60	/media/F	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=25a3efad-a268-4380-923f-257a39ec14fc	none	swap	sw	0	0



=================== sdb4: Location of files loaded by Grub: ===================


 975.5GB: boot/grub/core.img
 978.1GB: boot/grub/grub.cfg
 981.4GB: boot/initrd.img-2.6.32-25-generic
 972.8GB: boot/initrd.img-2.6.35-28-generic
 976.8GB: boot/initrd.img-2.6.38-8-generic
 975.8GB: boot/vmlinuz-2.6.32-25-generic
 976.1GB: boot/vmlinuz-2.6.35-28-generic
 979.1GB: boot/vmlinuz-2.6.38-8-generic
 976.8GB: initrd.img
 972.8GB: initrd.img.old
 979.1GB: vmlinuz
 976.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  87 b5 df ca 0d 94 f2 a4  a5 78 d8 09 a0 08 c0 00  |.........x......|
00000010  00 01 08 1b 7f 0f db fa  70 80 83 f8 20 83 fa e0  |........p... ...|
00000020  9b fc f4 8a 49 f2 00 18  37 f3 1d bf a6 b2 02 0f  |....I...7.......|
00000030  e0 82 0f eb d0 4c fe 90  03 92 4f 90 00 c1 bd 18  |.....L....O.....|
00000040  08 5f e3 44 12 54 90 dc  80 86 00 de 6d be 90 08  |._.D.T......m...|
00000050  60 0d 36 00 0c 8d 6f cd  c0 38 bf 40 4d 00 3f 22  |`.6...o..8.@M.?"|
00000060  43 7e 87 42 74 7b 7e 7d  a0 84 01 20 06 40 9a 00  |C~.Bt{~}... .@..|
00000070  b3 1b a0 10 c0 52 20 26  7f e9 84 86 40 87 fe e0  |.....R &....@...|
00000080  02 c6 dd 1a 18 d5 00 e1  5a c8 4d 3a b5 38 53 7c  |........Z.M:.8S||
00000090  b9 a8 a4 a6 f4 87 35 0b  0c db d5 93 75 2d aa 91  |......5.....u-..|
000000a0  2c 96 1f 4b 44 3e b7 3a  e5 fe 41 32 58 b1 24 b3  |,..KD>.:..A2X.$.|
000000b0  0d b2 55 0d c9 49 0d d0  8a 46 b2 49 b1 25 b6 c2  |..U..I...F.I.%..|
000000c0  ac b6 14 72 c6 c2 97 e9  39 b6 48 90 b4 93 64 b6  |...r....9.H...d.|
000000d0  14 7d 8a 73 73 3a 93 a9  cb 69 69 65 4b 25 85 96  |.}.ss:...iieK%..|
000000e0  b2 2a 01 4d 68 69 45 45  b4 ab 55 20 c0 da d4 3f  |.*.MhiEE..U ...?|
000000f0  1a 80 83 fd 60 07 f4 93  80 03 04 6e f6 97 1b 86  |....`......n....|
00000100  80 02 12 08 00 c3 c8 00  60 8d dc 87 c5 6c 15 69  |........`....l.i|
00000110  4d ab 67 1a ac df a5 65  18 d6 42 da c3 40 07 0d  |M.g....e..B..@..|
00000120  2a d4 2b 1f 2f 32 ad ca  ab 25 96 55 94 ea 5c b6  |*.+./2...%.U..\.|
00000130  35 d1 1f 32 49 2d 42 ad  59 12 da b0 a8 a3 5a 93  |5..2I-B.Y.....Z.|
00000140  2f 99 d2 45 4b 24 91 52  44 a5 d2 9a d7 2d b2 e5  |/..EK$.RD....-..|
00000150  96 52 ad 96 49 4a 0d a9  5b 43 4d a5 58 75 8b 93  |.R..IJ..[CM.Xu..|
00000160  4a b6 52 8b 55 b5 0e 1c  ca 29 50 b2 c2 0e 0a 92  |J.R.U....)P.....|
00000170  36 d3 52 c9 0f 2c b9 0a  89 69 74 b5 b4 e6 bd f2  |6.R..,...it.....|
00000180  5c 7c 96 ca 7d ab 65 92  42 8f 28 7b 51 96 f3 b5  |\|..}.e.B.({Q...|
00000190  56 14 7c b4 e4 89 4f 48  da 29 55 64 aa 5c b2 d2  |V.|...OH.)Ud.\..|
000001a0  45 b1 9c d3 65 92 24 a9  4b 92 d5 48 b0 b8 92 8c  |E...e.$.K..H....|
000001b0  69 42 a5 18 72 4a 52 0c  18 53 50 f4 00 4f 00 fe  |iB..rJR..SP..O..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 36 5e 2c 00 00 00  |..........6^,...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

And here's the output running the script on 11.04:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdb4 ya está montado o sdb4 está ocupado

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   167,798,924   167,798,862   7 HPFS/NTFS
/dev/sda2    *    167,798,928   276,925,120   109,126,193   7 HPFS/NTFS
/dev/sda3         276,926,464   312,580,095    35,653,632  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,884,028,227 1,884,028,165   7 HPFS/NTFS
/dev/sdb2       1,917,582,660 1,950,612,299    33,029,640  83 Linux
/dev/sdb3       1,950,612,361 1,953,520,064     2,907,704   5 Extended
/dev/sdb5       1,950,612,363 1,953,520,064     2,907,702  82 Linux swap / Solaris
/dev/sdb4    *  1,884,028,928 1,917,581,311    33,552,384  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5F0AADA934058B60                       ntfs       F                             
/dev/sda2        686ADC9E6ADC6A78                       ntfs       C                             
/dev/sda3        88513ffd-bfcf-4235-a8cc-0de32282ecad   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        062E615E2E6147AF                       ntfs       Archivos                      
/dev/sdb2        ba217d41-c214-4595-8265-e5884dea3f81   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        88513ffd-bfcf-4235-a8cc-0de32282ecad   ext4                                     
/dev/sdb5        25a3efad-a268-4380-923f-257a39ec14fc   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Archivos          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/C                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/F                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(3)\windows
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\windows="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
set locale_dir=($root)/boot/grub/locale
set lang=es_AR
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
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
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, con Linux 2.6.38-8-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.35-28-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos4)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 5F0AADA934058B60
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 686ADC9E6ADC6A78
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro ipv6.disable=1 quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro single ipv6.disable=1
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro ipv6.disable=1 quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 65d12214-1afe-42fd-a67f-5e17456ac759
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=65d12214-1afe-42fd-a67f-5e17456ac759 ro single ipv6.disable=1
	initrd /boot/initrd.img-2.6.32-24-generic
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb4 :
UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=062E615E2E6147AF	/media/Archivos	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=686ADC9E6ADC6A78	/media/C	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=5F0AADA934058B60	/media/F	ntfs-3g	defaults,uid=1000,locale=es_AR.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=25a3efad-a268-4380-923f-257a39ec14fc	none	swap	sw	0	0



=================== sda3: Location of files loaded by Grub: ===================


 152.6GB: boot/grub/core.img
 155.2GB: boot/grub/grub.cfg
 158.6GB: boot/initrd.img-2.6.32-25-generic
 150.0GB: boot/initrd.img-2.6.35-28-generic
 154.0GB: boot/initrd.img-2.6.38-8-generic
 153.0GB: boot/vmlinuz-2.6.32-25-generic
 153.3GB: boot/vmlinuz-2.6.35-28-generic
 156.3GB: boot/vmlinuz-2.6.38-8-generic
 154.0GB: initrd.img
 150.0GB: initrd.img.old
 156.3GB: vmlinuz
 153.3GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
set locale_dir=($root)/boot/grub/locale
set lang=es
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb2) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba217d41-c214-4595-8265-e5884dea3f81 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set ba217d41-c214-4595-8265-e5884dea3f81
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5f0aada934058b60
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 686adc9e6adc6a78
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, con Linux 2.6.38-8-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, con Linux 2.6.38-8-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, con Linux 2.6.35-28-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, con Linux 2.6.35-28-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, con Linux 2.6.32-25-generic (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, con Linux 2.6.32-25-generic (modo recuperación) (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 88513ffd-bfcf-4235-a8cc-0de32282ecad
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=88513ffd-bfcf-4235-a8cc-0de32282ecad ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=ba217d41-c214-4595-8265-e5884dea3f81 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=25a3efad-a268-4380-923f-257a39ec14fc none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 986.2GB: boot/grub/core.img
 993.2GB: boot/grub/grub.cfg
 986.2GB: boot/initrd.img-2.6.32-21-generic
 986.2GB: boot/vmlinuz-2.6.32-21-generic
 986.2GB: initrd.img
 986.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  87 b5 df ca 0d 94 f2 a4  a5 78 d8 09 a0 08 c0 00  |.........x......|
00000010  00 01 08 1b 7f 0f db fa  70 80 83 f8 20 83 fa e0  |........p... ...|
00000020  9b fc f4 8a 49 f2 00 18  37 f3 1d bf a6 b2 02 0f  |....I...7.......|
00000030  e0 82 0f eb d0 4c fe 90  03 92 4f 90 00 c1 bd 18  |.....L....O.....|
00000040  08 5f e3 44 12 54 90 dc  80 86 00 de 6d be 90 08  |._.D.T......m...|
00000050  60 0d 36 00 0c 8d 6f cd  c0 38 bf 40 4d 00 3f 22  |`.6...o..8.@M.?"|
00000060  43 7e 87 42 74 7b 7e 7d  a0 84 01 20 06 40 9a 00  |C~.Bt{~}... .@..|
00000070  b3 1b a0 10 c0 52 20 26  7f e9 84 86 40 87 fe e0  |.....R &....@...|
00000080  02 c6 dd 1a 18 d5 00 e1  5a c8 4d 3a b5 38 53 7c  |........Z.M:.8S||
00000090  b9 a8 a4 a6 f4 87 35 0b  0c db d5 93 75 2d aa 91  |......5.....u-..|
000000a0  2c 96 1f 4b 44 3e b7 3a  e5 fe 41 32 58 b1 24 b3  |,..KD>.:..A2X.$.|
000000b0  0d b2 55 0d c9 49 0d d0  8a 46 b2 49 b1 25 b6 c2  |..U..I...F.I.%..|
000000c0  ac b6 14 72 c6 c2 97 e9  39 b6 48 90 b4 93 64 b6  |...r....9.H...d.|
000000d0  14 7d 8a 73 73 3a 93 a9  cb 69 69 65 4b 25 85 96  |.}.ss:...iieK%..|
000000e0  b2 2a 01 4d 68 69 45 45  b4 ab 55 20 c0 da d4 3f  |.*.MhiEE..U ...?|
000000f0  1a 80 83 fd 60 07 f4 93  80 03 04 6e f6 97 1b 86  |....`......n....|
00000100  80 02 12 08 00 c3 c8 00  60 8d dc 87 c5 6c 15 69  |........`....l.i|
00000110  4d ab 67 1a ac df a5 65  18 d6 42 da c3 40 07 0d  |M.g....e..B..@..|
00000120  2a d4 2b 1f 2f 32 ad ca  ab 25 96 55 94 ea 5c b6  |*.+./2...%.U..\.|
00000130  35 d1 1f 32 49 2d 42 ad  59 12 da b0 a8 a3 5a 93  |5..2I-B.Y.....Z.|
00000140  2f 99 d2 45 4b 24 91 52  44 a5 d2 9a d7 2d b2 e5  |/..EK$.RD....-..|
00000150  96 52 ad 96 49 4a 0d a9  5b 43 4d a5 58 75 8b 93  |.R..IJ..[CM.Xu..|
00000160  4a b6 52 8b 55 b5 0e 1c  ca 29 50 b2 c2 0e 0a 92  |J.R.U....)P.....|
00000170  36 d3 52 c9 0f 2c b9 0a  89 69 74 b5 b4 e6 bd f2  |6.R..,...it.....|
00000180  5c 7c 96 ca 7d ab 65 92  42 8f 28 7b 51 96 f3 b5  |\|..}.e.B.({Q...|
00000190  56 14 7c b4 e4 89 4f 48  da 29 55 64 aa 5c b2 d2  |V.|...OH.)Ud.\..|
000001a0  45 b1 9c d3 65 92 24 a9  4b 92 d5 48 b0 b8 92 8c  |E...e.$.K..H....|
000001b0  69 42 a5 18 72 4a 52 0c  18 53 50 f4 00 4f 00 fe  |iB..rJR..SP..O..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 36 5e 2c 00 00 00  |..........6^,...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

As you can see, they show contradictory information: running it on 10.10 says 10.10 is installed on sda3 and 11.04 is installed on sdb4; while running it on 11.04 says 11.04 is installed on sda3.

---

### Post by Hedgehog1 on 2011-05-09
Well, this is an interesting challenge.

The references to your drive being different depending on with OS you select is annoying, but not unexpected.  Because your two Ubuntu installs are on different disks, the disk where the OS lives is assigned the /dev/sda value when it boots.

It is because the /sda, /sdb (and so on) can fluctuate that I prefer to always use UUIDs to reference partition, as UUIDs do not change.

Now to your issue:

Once the 11.04 and Mint installs are removed, and a fresh 'sudo update-grub' is run, you will boot into 10.10 from grub every time.

Please boot into 10.10, and the run Gparted If you don't have it loaded on your 10.10 install, you can get it from the Ubuntu Software Center.

In Gparted, select the drive with Mint and 11.04 on it.  This should be the /dev/sdb disk.

Delete the /dev/sdb4, sdb5, sdb3 and sdb2 partitons from that drive.  This will leave you with only a single /dev/sdb1 NTFS partition - one you can expand later to use the whole disk.

Once the partitions have been deleted, run this command again:

```
sudo update-grub
```

Now when you reboot, you should only boot into Windows, or Ubuntu 10.10.

You can then expand the /dev/sdb1 NTFS partiton to fill the desk using the Disk Management function in Windows, or using gparted from Ubuntu.


***The Hedge***

:KS

---

### Post by Mauricio_A on 2011-05-09
Are you sure 10.10 is on sda3? I'd hate deleting the wrong partition. Is there anything else I can do, like hiding the partitions or something like that, check if it works and then delete them?

Also, the problem seems to have changed a little now: the first option (latest kernel) takes me to 11.04 every time now, and choosing the second kernel takes me to 10.10. I have to go to work now and don't have time to do anything now, will continue tonight.

EDIT: I can't delete sdb4 using GParted from 10.10 because it's mounted and it won't let me unmount it (both sda3 and sdb4 have / as mounting point). If I'm going to delete sdb4 I'll have to use a live CD and open GParted from there.

---

### Post by LostFarmer on 2011-05-09
One problem is both sdb4 and sda3 have the same UUID.

---

### Post by Mauricio_A on 2011-05-09
> **LostFarmer said:**
> One problem is both sdb4 and sda3 have the same UUID.

Any idea on how to solve this?

---

### Post by Mauricio_A on 2011-05-09
Opening my computer and disconnecting the hard drives manually I'm now convinced 10.10 is definitely on sda.
Deleting the sdb4 partition is definitely the way to go.

---

### Post by Hedgehog1 on 2011-05-09
Just logged on (after another fun day at the office).  Disconnecting the hard drive as an 'absolute' test is perfect; great thinking!

***The Hedge***

:KS

---

### Post by Mauricio_A on 2011-05-10
Great, that solved the problem.
Thanks for the help!

---

