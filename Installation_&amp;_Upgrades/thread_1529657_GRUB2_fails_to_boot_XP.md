---
title: "GRUB2 fails to boot XP"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by expatal on 2010-07-12
Having installed 10.04 Lucid in the '/' partition of my HD, while retaining my working '/home' partition, previously under Karmic, it is now impossible to boot into an existing Windows XP partition through the GRUB2 (1.98-1ubuntu6) menu. The menu entry is correctly generated in grub.cfg, but when selected, the following message appears:

```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```

I have spent hours combing Ubuntu forums, Wikis and Launchpad bugs without finding a problem which resembles mine.

I have compared RESULTS.txt output from the boot_info_script055.sh script with many of those posted in the above threads, but nothing seems to be wrong with my installation, especially concerning GRUB2 being installed in the XP partition (not my case).

The testdisk (v. 6.11-1) utility showed no errors in the XP partition.

I then rendered the XP partition directly bootable (without GRUB2) by overwriting the MBR using an XP installation CD (fixboot and fixmbr commands in recovery console), and XP booted fine. After reinstalling GRUB2 on the MBR however (`sudo update-grub' from a live Lucid CD), the situation reverted to not being able to boot XP from the GRUB2 menu (same error message as above: Reboot and Select proper Boot device...).

I'd be most grateful for any advice you can offer or any bug reference to this exact problem (if such exists).

Attached:
- output from `fdisk -l',
- from boot_info_script055 (RESULTS.txt)
- /boot/grub/grub.cfg

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x903a730e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3113    25005141    7  HPFS/NTFS
/dev/sda2            3114       18813   126110219+   5  Extended
/dev/sda3           18814       19451     5124735   1c  Hidden W95 FAT32 (LBA)
/dev/sda4           19452       19457       48195   ef  EFI (FAT-12/16/32)
/dev/sda5            3114        7854    38082051   83  Linux
/dev/sda6            7855        7976      979933+  82  Linux swap / Solaris
/dev/sda7            7977       18686    86028043+  83  Linux
/dev/sda8           18687       18813     1020096   82  Linux swap / Solaris

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders
Units = cylinders of 810 * 512 = 414720 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa32fa32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              11       19166     7757824    b  W95 FAT32

```
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    50,010,344    50,010,282   7 HPFS/NTFS
/dev/sda2          50,010,406   302,230,844   252,220,439   5 Extended
/dev/sda5          50,010,408   126,174,509    76,164,102  83 Linux
/dev/sda6         126,174,573   128,134,439     1,959,867  82 Linux swap / Solaris
/dev/sda7         128,134,503   300,190,589   172,056,087  83 Linux
/dev/sda8         300,190,653   302,230,844     2,040,192  82 Linux swap / Solaris
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    15,523,839    15,515,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5C60BE8360BE6404                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8630c8f7-8a6f-49aa-b74e-4aad2554dd0b   ext4                                     
/dev/sda6        ef7f1486-9989-4939-b2c8-70441453f1ea   swap                                     
/dev/sda7        79c9ef95-0a4e-4f24-9cea-57ca4ab96580   ext4                                     
/dev/sda8        79176e55-08ff-477e-bb54-0baad71b8c6a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6439-3131                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sdb1        /media/6439-3131         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /noexecute=optin /fastdetect

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
search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
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
search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
set superusers="phoenadmin"
password phoenadmin twosheds
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os --users phoenadmin {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --users phoenadmin {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os --users phoenadmin {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --users phoenadmin {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5c60be8360be6404
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda3)" {
	insmod fat
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# added by A.S. May 17 '10
# source: http://ubuntuforums.org/showthread.php?t=1229345&page=47 post #461
insmod 915resolution
915resolution 5c 1366 768
set gfxmode=1366x768
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
UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=79c9ef95-0a4e-4f24-9cea-57ca4ab96580 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=ef7f1486-9989-4939-b2c8-70441453f1ea none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=79176e55-08ff-477e-bb54-0baad71b8c6a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  53.6GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
  53.6GB: boot/initrd.img-2.6.32-21-generic
  55.7GB: boot/initrd.img-2.6.32-22-generic
  53.6GB: boot/vmlinuz-2.6.32-21-generic
  55.7GB: boot/vmlinuz-2.6.32-22-generic
  55.7GB: initrd.img
  53.6GB: initrd.img.old
  55.7GB: vmlinuz
  53.6GB: vmlinuz.old
```

```
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
search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
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
search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
set superusers="phoenadmin"
password phoenadmin twosheds
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os --users phoenadmin {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --users phoenadmin {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os --users phoenadmin {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --users phoenadmin {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8630c8f7-8a6f-49aa-b74e-4aad2554dd0b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8630c8f7-8a6f-49aa-b74e-4aad2554dd0b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5c60be8360be6404
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda3)" {
	insmod fat
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# added by A.S. Jul 11 '10 -- same result as for automatic entry!
# source: http://ubuntuforums.org/showthread.php?p=8363434#post8363434 post #2
menuentry "Windows XP (on /dev/sda1) - customised version" {
insmod ntfs
set root=(hd0,1)
chainloader +1
}

# added by A.S. May 17 '10
# source: http://ubuntuforums.org/showthread.php?t=1229345&page=47 post #461
insmod 915resolution
915resolution 5c 1366 768
set gfxmode=1366x768
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.backup ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# added by A.S. May 17 '10
# source: http://ubuntuforums.org/showthread.php?t=1229345&page=47 post #461
insmod 915resolution
915resolution 5c 1366 768
set gfxmode=1366x768
### END /etc/grub.d/40_custom.backup ###
```

---

### Post by MAFoElffen on 2010-07-12
This is similar to a problem I'm having with Ubuntu 10.04 and it's Grub2 boot and menu also (another thread in same area).  Will subscribe to this thread and let you know if I come up with any resolution on mine.

Have you tried a Windows XP install disk using "Repair" instead of install or a Windows XP Rescue Disk?  Note- I used the Windows Vista and WIN7 "repair" on mine with no resolution... but I have both them installed on (hdx,1) (first partitions)of separate drives.

---

### Post by oldfred on 2010-07-12
Just for info the results.txt already includes grub.cfg and fdisk -lu.

I do not see anything wrong with your results.txt. And if you installed the windows boot loader to the MBR and it boots I do not understand why grub will not boot.

The only suggestion I can make is at the grub menu use e for edit and remove the search line and even try removing all lines except set root and chainload. Each red line should be optional info and system should boot without, so try editing one at a time or various combinations.

   [COLOR=DarkRed] insmod ntfs[/COLOR]
    set root='(hd0,1)'
    [COLOR=DarkRed]search --no-floppy --fs-uuid --set 5c60be8360be6404
    drivemap -s (hd0) ${root}[/COLOR]
    chainloader +1

Supposedly the latest version of grub already reads ntfs and old grub just chainloaded without reading the drive and if it did not work it did crash. Search is a backup to the set root. If drive order has changed so set root is not correct it should find the correct partition with the search command. Drivemap is when the install is not on the first drive and windows expects to be on the first drive. You hd0 should be the same as root so it is not mapping anything.

---

### Post by expatal on 2010-07-13
> **oldfred said:**
> 
...

The only suggestion I can make is at the grub menu use e for edit and remove the search line and even try removing all lines except set root and chainload. Each red line should be optional info and system should boot without, so try editing one at a time or various combinations.

   [COLOR=DarkRed] insmod ntfs[/COLOR]
    set root='(hd0,1)'
    [COLOR=DarkRed]search --no-floppy --fs-uuid --set 5c60be8360be6404
    drivemap -s (hd0) ${root}[/COLOR]
    chainloader +1

Supposedly the latest version of grub already reads ntfs and old grub just chainloaded without reading the drive and if it did not work it did crash. Search is a backup to the set root. If drive order has changed so set root is not correct it should find the correct partition with the search command. Drivemap is when the install is not on the first drive and windows expects to be on the first drive. You hd0 should be the same as root so it is not mapping anything.

@oldfred: Thanks for that. I did as you suggested, but nothing changed.

Editing the GRUB menu, I tried the following combination:

```
set root='(hd0,1)'
chainloader +1
```

Then, just to see:

```
insmod ntfs
set root='(hd0,1)'
chainloader +1
```

Same error message appears:

```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```

So, still no way, via GRUB2, into the originally preinstalled XP on this laptop.

One thought: I did have Karmic installed for a few weeks on the laptop concerned (probably using the 1.97 GRUB2), but am not sure if I ever tried to boot into XP under it. However, I still have a desktop under Karmic using grub-pc version 1.97~beta4-1ubuntu4.1 which boots fine into the original XP system.

In any case, thanks for you help!

---

### Post by oldfred on 2010-07-13
I do not recognize that error as a grub error is it a windows error and grub is booting your windows, it is just windows that is not working?

---

### Post by kansasnoob on 2010-07-13
While this should have no direct impact on booting Windows I noticed one thing:

> ### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[B][COLOR="Red"]# added by A.S. May 17 '10
# source: [http://ubuntuforums.org/showthread.php?t=1229345&page=47](http://ubuntuforums.org/showthread.php?t=1229345&page=47) post #461
insmod 915resolution
915resolution 5c 1366 768
set gfxmode=1366x768[/COLOR][/B]
### END /etc/grub.d/40_custom ###

That leads me to believe that it's possible some other grub2 files could be messed up. Can you explain why that was edited in that manner?

Regardless I assume you know quite well how to restore either the Windows mbr or the grub2 mbr from what you've said above, and I see at the time you ran the Boot Info Script you had a grub2 mbr, but just to recap:

You can restore a "generic" Windows mbr using only an Ubuntu Live CD and running the following commands:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

And you can always recover the grub2 mbr using a Live CD and running:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

And if that should ever return any errors also:

```
grub-install --recheck /dev/sda
```

And you may (or may not) want to "update-grub":

```
update-grub
```

Then exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

I just wanted to repeat that so you can easily copy-n-paste from here as we test things :)

Anyway I'd begin by booting into Ubuntu (not just the Live CD) and running:

```
aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

That should show something like this:

> lance@lance-desktop:~$ aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed


You'll notice that shows the package "grub" is NOT installed, but the packages "grub-pc", "grub-common", and "os-prober" are installed. If that's not correct I need to know, but if it is correct I'd begin by creating an entirely knew grub configuration by running these commands from your installed Lucid:

```
sudo mv /boot/grub /boot/grub_old
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub-pc grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

Then see if both Ubuntu and Windows will boot, if so great, if not I'm stumped other than possibly reverting to legacy grub :(

You would then have to manually add Windows to it's menu.lst but let's see where this leads us first.

---

### Post by expatal on 2010-07-13
> **kansasnoob said:**
> While this should have no direct impact on booting Windows I noticed one thing:



That leads me to believe that it's possible some other grub2 files could be messed up. Can you explain why that was edited in that manner?

Regardless I assume you know quite well how to restore either the Windows mbr or the grub2 mbr from what you've said above, and I see at the time you ran the Boot Info Script you had a grub2 mbr, but just to recap:

You can restore a "generic" Windows mbr using only an Ubuntu Live CD and running the following commands:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

And you can always recover the grub2 mbr using a Live CD and running:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

And if that should ever return any errors also:

```
grub-install --recheck /dev/sda
```

And you may (or may not) want to "update-grub":

```
update-grub
```

Then exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

I just wanted to repeat that so you can easily copy-n-paste from here as we test things :)

Anyway I'd begin by booting into Ubuntu (not just the Live CD) and running:

```
aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

That should show something like this:



You'll notice that shows the package "grub" is NOT installed, but the packages "grub-pc", "grub-common", and "os-prober" are installed. If that's not correct I need to know, but if it is correct I'd begin by creating an entirely knew grub configuration by running these commands from your installed Lucid:

```
sudo mv /boot/grub /boot/grub_old
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub-pc grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

Then see if both Ubuntu and Windows will boot, if so great, if not I'm stumped other than possibly reverting to legacy grub :(

You would then have to manually add Windows to it's menu.lst but let's see where this leads us first.

@kansasnoob: Many thanks for your advice.

I won't have time tonight to try everything out, but have already established, using your script, that the following apply:

Legacy grub NOT installed;
grub-pc installed;
grub-common installed;
os-prober installed.

```
# added by A.S. May 17 '10
# source: http://ubuntuforums.org/showthread.p...229345&page=47 post #461
insmod 915resolution
...
```
The above 40_custom additions for screen resolution were added to alleviate a video-driver problem for the laptop concerned (EeePC 1101HA w/ Intel GMA500 video chipset, not supported in Ubuntu). In fact, I have since installed a reasonably satisfactory 2D-driver solution and no longer need this customisation, so will remove, it as a first experiment.

If that has no effect, I will then recreate a new grub-pc environment from my installed Lucid according to your instructions and report back.

Once again, many thanks.

---

### Post by expatal on 2010-07-14
> **expatal said:**
> @kansasnoob: Many thanks for your advice.

I won't have time tonight to try everything out, but have already established, using your script, that the following apply:

Legacy grub NOT installed;
grub-pc installed;
grub-common installed;
os-prober installed.

```
# added by A.S. May 17 '10
# source: http://ubuntuforums.org/showthread.p...229345&page=47 post #461
insmod 915resolution
...
```

The above 40_custom additions for screen resolution were added to alleviate a video-driver problem for the laptop concerned (EeePC 1101HA w/ Intel GMA500 video chipset, not supported in Ubuntu). In fact, I have since installed a reasonably satisfactory 2D-driver solution and no longer need this customisation, so will remove it as a first experiment.



Good news, the first experiment worked. After removing the lines from /etc/grub.d/40_custom relating to screen resolution problems on my Eee PC laptop (see above), applying `sudo update-grub' and rebooting, XP came up like a charm.

I would be interested to know how such a customization might have affected the action of GRUB2 in this way. In any case, it shouldn't have done (bug?).

---

### Post by dsojourner on 2010-10-23
Thanks for this thread!

I found I was able to keep the 915resolution lines by adding them in the linux specific menu entries, rather than in the boot menu as a whole -- for any people who find this and for what ever reason do not want to switch the video driver.

---

