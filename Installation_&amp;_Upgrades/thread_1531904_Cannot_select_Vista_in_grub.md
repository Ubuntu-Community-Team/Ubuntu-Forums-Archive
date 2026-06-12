---
title: "Cannot select Vista in grub"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by bobterri73 on 2010-07-15
HELP!!

I just upgraded to Ubuntu 10.04 from 9.10.  Under 9.10 I dual booted to Ubuntu or Vista in the grub menu.  Now that I have upgraded I cannot boot to Vista.  When I select the Vista option in the Grub bootloader it restarts the computer and comes back to the grub menu screen again.  

I have run the boot_info_script.  The results are:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks at sector 131826747 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 131815603 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 131815603 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 131815603 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 131815603 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 131826747 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 131826747 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    14,329,979    14,329,917  12 Compaq diagnostics
/dev/sda2    *     14,331,904   131,530,743   117,198,840   7 HPFS/NTFS
/dev/sda3         246,460,416   312,578,047    66,117,632   7 HPFS/NTFS
/dev/sda4         131,540,220   246,453,164   114,912,945   5 Extended
/dev/sda5         131,540,283   243,850,634   112,310,352  83 Linux
/dev/sda6         243,850,698   246,453,164     2,602,467  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdb5              16,128 1,953,520,064 1,953,503,937   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 513 MB, 513802240 bytes
16 heads, 32 sectors/track, 1960 cylinders, total 1003520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     1,003,519     1,003,488   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A20C425816D9B5D2                       ntfs       PQSERVICE                     
/dev/sda2        A61655E91655BB4F                       ntfs       VistaStorage                  
/dev/sda3        4E5CE2385CE21B0B                       ntfs       VistaProgram                  
/dev/sda4: PTTYPE="dos" 
/dev/sda5        dbd09686-39d0-4859-87fa-1b2084a7573c   ext4                                     
/dev/sda6        f0ce004c-c85a-4a52-9b34-9d93d4f2ef20   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        A784-F191                              vfat       Teradrive                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0C98-1CE1                              vfat       TRAVELDRIVE                   
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/TRAVELDRIVE       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set dbd09686-39d0-4859-87fa-1b2084a7573c
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
search --no-floppy --fs-uuid --set dbd09686-39d0-4859-87fa-1b2084a7573c
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set dbd09686-39d0-4859-87fa-1b2084a7573c
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=dbd09686-39d0-4859-87fa-1b2084a7573c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set dbd09686-39d0-4859-87fa-1b2084a7573c
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=dbd09686-39d0-4859-87fa-1b2084a7573c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set dbd09686-39d0-4859-87fa-1b2084a7573c
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=dbd09686-39d0-4859-87fa-1b2084a7573c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set dbd09686-39d0-4859-87fa-1b2084a7573c
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=dbd09686-39d0-4859-87fa-1b2084a7573c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set dbd09686-39d0-4859-87fa-1b2084a7573c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set dbd09686-39d0-4859-87fa-1b2084a7573c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a20c425816d9b5d2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4e5ce2385ce21b0b
	chainloader +1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=dbd09686-39d0-4859-87fa-1b2084a7573c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f0ce004c-c85a-4a52-9b34-9d93d4f2ef20 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  67.4GB: boot/grub/core.img
  67.6GB: boot/grub/grub.cfg
  77.0GB: boot/initrd.img-2.6.31-22-generic
  77.1GB: boot/initrd.img-2.6.32-23-generic
  74.8GB: boot/vmlinuz-2.6.31-22-generic
  76.8GB: boot/vmlinuz-2.6.32-23-generic
  77.1GB: initrd.img
  77.0GB: initrd.img.old
  76.8GB: vmlinuz
  74.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

---

### Post by oldfred on 2010-07-16
I see two issues. You installed grub everywhere.

When the instructions said all drives they meant sda, sdb etc not partitions sda1, sda2 sdb1 etc. You overwrote the windows boot sector in the windows partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Also you have the boot flag on sda2, but it is missing 
 /Boot/BCD

Is sda2 your Vista install or is sda3 which looks like it has all your files to boot? Grub will not care about the boot flag, but windows repairs or if you want to directly boot Vista the flag has to be on the correct partition.

---

### Post by bobterri73 on 2010-07-16
Thank you Thank you  THANK YOU!!  Your information led me to the solution.  I can now boot to Vista.  I really wish the instructions had been more specific when it asked me to select where to install the Grub.

My Vista program is in sda3.  thanks for pointing out that the boot flag is in the wrong place.  I am going to check the man pages to see how to get that corrected.  Thanks again so much.
Bob

---

### Post by oldfred on 2010-07-16
Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.

You can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

---

