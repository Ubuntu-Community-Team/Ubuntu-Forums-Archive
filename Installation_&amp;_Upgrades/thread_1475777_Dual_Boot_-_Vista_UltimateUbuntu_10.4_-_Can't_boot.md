---
title: "Dual Boot - Vista Ultimate/Ubuntu 10.4 - Can't boot Windows"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by smithmum on 2010-05-07
I have just installed Ubuntu 10.4 x64 onto a machine with Vista Ultimate x64. When I boot the machine, the Windows option comes up in the GRUB menu. However, when I attempt to boot Windows, I receive the following error:

    error: No such device: de80ab9f80ab7d21.
    error: No such partition.
    Press any key to continue...

I looked around and found a similar issue at [http://ubuntuforums.org/showthread.php?t=1466230](http://ubuntuforums.org/showthread.php?t=1466230)

However, before trying to fix the issue by guesswork or via solutions that worked for a similar, though not necessarily identical problem, I thought I'd post here an ask for help.

I've run the boot info script (see output below) mentioned several places on this site as a valuable input for boot problem tracking.

Any ideas on how to get Windows to boot on my computer?

OUTPUT FROM BOOT_INFO_SCRIPT055

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
209 heads, 16 sectors/track, 1168369 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 3,907,028,991 3,907,026,944   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34       262,177       262,144 Microsoft Windows
/dev/sdb2         264,192 1,843,464,191 1,843,200,000 Linux or Data
/dev/sdb3   1,843,464,192 1,859,088,383    15,624,192 Linux Swap
/dev/sdb4   1,859,088,384 3,907,026,943 2,047,938,560 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DE80AB9F80AB7D21                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2        7E7C8E987C8E4B3B                       ntfs       Flirt_Data                    
/dev/sdb3        a2c197ba-877d-49dc-b15f-01db4b06ac17   swap                                     
/dev/sdb4        2cc52ed1-9c66-4947-a303-4871e8cffe7d   ext4                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb4        /                        ext4       (rw,errors=remount-ro)
/dev/sdb2        /media/Flirt_Data        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/DE80AB9F80AB7D21  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set 2cc52ed1-9c66-4947-a303-4871e8cffe7d
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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set 2cc52ed1-9c66-4947-a303-4871e8cffe7d
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 2cc52ed1-9c66-4947-a303-4871e8cffe7d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=2cc52ed1-9c66-4947-a303-4871e8cffe7d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 2cc52ed1-9c66-4947-a303-4871e8cffe7d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=2cc52ed1-9c66-4947-a303-4871e8cffe7d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 2cc52ed1-9c66-4947-a303-4871e8cffe7d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=2cc52ed1-9c66-4947-a303-4871e8cffe7d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 2cc52ed1-9c66-4947-a303-4871e8cffe7d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=2cc52ed1-9c66-4947-a303-4871e8cffe7d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 2cc52ed1-9c66-4947-a303-4871e8cffe7d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 2cc52ed1-9c66-4947-a303-4871e8cffe7d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de80ab9f80ab7d21
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=2cc52ed1-9c66-4947-a303-4871e8cffe7d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=a2c197ba-877d-49dc-b15f-01db4b06ac17 none            swap    sw              0       0

=================== sdb4: Location of files loaded by Grub: ===================


1564.0GB: boot/grub/core.img
1246.3GB: boot/grub/grub.cfg
1564.0GB: boot/initrd.img-2.6.32-21-generic
1564.1GB: boot/initrd.img-2.6.32-22-generic
1564.0GB: boot/vmlinuz-2.6.32-21-generic
 952.1GB: boot/vmlinuz-2.6.32-22-generic
1564.1GB: initrd.img
1564.0GB: initrd.img.old
 952.1GB: vmlinuz
1564.0GB: vmlinuz.old

===END===

---

### Post by oldfred on 2010-05-07
You do not have the common problem of grub installed to the windows partition.

You do not have a boot flag ( but I do not think that is the main problem). Windows requires a boot flag to find the active partition. Linux/grub does not require a boot flag but some BIOS (windows assumed?) require a boot flag on a primary partitition.

You can use gparted, Disk Utility or command line to set boot flag on sda1. I am not sure if gparted will work on sdb as it has gpt. You should download gdisk, I think?
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I have seen where just editing out the search line works. Try editing the boot line and remove the entire search line.

---

