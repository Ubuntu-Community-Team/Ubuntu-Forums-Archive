---
title: "Windows 7 won't boot after Ubuntu 10.04 installation..."
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by twgray on 2010-08-25
I have just installed Ubuntu 10.04 on the second harddrive in my Acer Aspire 8943G laptop.  I installed Grub2 into the MBR of the Windows drive.  After rebooting, the grub menu comes up with:

Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32.24-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows 7 (loader)  (on /dev/sda3)

Selecting Windows 7 gives the following error:

error:  no such device: F2CAB9B7CAB97905 
error:  no such partition

Press any key to continue...

Selecting Windows Vista gives a similar error.

I have run the boot_info-script giving the following:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 25438032 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,410,751    30,408,704  27 Hidden HPFS/NTFS
/dev/sda2          30,410,752    37,750,783     7,340,032  12 Compaq diagnostics
/dev/sda3    *     37,750,784    37,955,583       204,800   7 HPFS/NTFS
/dev/sda4          37,955,584   976,771,071   938,815,488   f W95 Ext d (LBA)
/dev/sda5          37,957,632   976,771,071   938,813,440   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048   625,106,943   625,104,896 Linux or Data
/dev/sdb2     625,106,944   625,141,759        34,816 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6C22B6EA22B6B882                       ntfs       PQSERVICE                     
/dev/sda2        4C98B84998B832F6                       ntfs       ARCADE                        
/dev/sda3        F2CAB9B7CAB97905                       ntfs       SYSTEM RESERVED               
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0E2413FC2413E60D                       ntfs       Acer                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        766d5b15-0ee1-48a9-a4fe-3439a014c1c0   ext4                                     
/dev/sdb2        49e47286-a5c5-4744-a6e6-5dbb9aa5b2b8   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 766d5b15-0ee1-48a9-a4fe-3439a014c1c0
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 766d5b15-0ee1-48a9-a4fe-3439a014c1c0
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 766d5b15-0ee1-48a9-a4fe-3439a014c1c0
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=766d5b15-0ee1-48a9-a4fe-3439a014c1c0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 766d5b15-0ee1-48a9-a4fe-3439a014c1c0
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=766d5b15-0ee1-48a9-a4fe-3439a014c1c0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 766d5b15-0ee1-48a9-a4fe-3439a014c1c0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 766d5b15-0ee1-48a9-a4fe-3439a014c1c0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6c22b6ea22b6b882
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set f2cab9b7cab97905
	chainloader +1
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=766d5b15-0ee1-48a9-a4fe-3439a014c1c0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=49e47286-a5c5-4744-a6e6-5dbb9aa5b2b8 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  98.9GB: boot/grub/core.img
  94.6GB: boot/grub/grub.cfg
  98.9GB: boot/initrd.img-2.6.32-24-generic
  98.9GB: boot/vmlinuz-2.6.32-24-generic
  98.9GB: initrd.img
  98.9GB: vmlinuz

```

I have deleted the grub uuid line:

	search --no-floppy --fs-uuid --set f2cab9b7cab97905

to no effect.

Help???

---

### Post by phillw on 2010-08-25
Hi,

I'd suggest following > How to restore the Windows Vista or 7 bootloader at [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) to get windows 'happy', then follow > How to restore the Ubuntu grub bootloader (9.10 and beyond) to put grub back on once windows is happy.

Regards,

Phill.

---

### Post by oldfred on 2010-08-25
You also have a mix of msdos (MBR) and gpt partition types.

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by twgray on 2010-08-27
The GRUB_PRELOAD_MODULES="part_msdos" did the trick.  I ultimately installed grub on the second harddrive and left the Windoze drive untouched.  I chose to boot the second drive by default in the bios.  Everything works now, but Ubuntu still boots erratically.  Grub starts up but when I select Ubuntu it goes to a blank screen with a blinking cursor about 75% of the time.  

Thanks for the help.

---

