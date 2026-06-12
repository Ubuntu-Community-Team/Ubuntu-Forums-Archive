---
title: "Dual boot windows vista / Lucid 10.04, grub doesnt see Windows"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by mario-huizar on 2010-05-07
HEllo all,

I had 9.10 installed and I did an upgrade to 10.04. However I cannot see anymore my Windows Vista partition with grub.. I have a Toshiba laptop Satellite p305.

This is my boot script output: Any hint will be appreciated..

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 519888342 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 519873518 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 519873750 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,088   519,590,294   516,516,207   7 HPFS/NTFS
/dev/sda3         519,590,295   625,137,344   105,547,050   5 Extended
/dev/sda5         519,590,358   620,735,534   101,145,177  83 Linux
/dev/sda6         620,735,598   625,137,344     4,401,747  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B89E85849E853BBE                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        F4E8B4F6E8B4B866                       ntfs       Mario                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        05256b8a-fb03-4e43-9814-b7c698a5e8c8   ext4                                     
/dev/sda6        8de50eea-fb00-4bfb-8237-a46183255d80   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=05256b8a-fb03-4e43-9814-b7c698a5e8c8

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		05256b8a-fb03-4e43-9814-b7c698a5e8c8
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		05256b8a-fb03-4e43-9814-b7c698a5e8c8
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		05256b8a-fb03-4e43-9814-b7c698a5e8c8
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		05256b8a-fb03-4e43-9814-b7c698a5e8c8
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Chainload into GRUB 2
root		05256b8a-fb03-4e43-9814-b7c698a5e8c8
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		05256b8a-fb03-4e43-9814-b7c698a5e8c8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
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
search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f4e8b4f6e8b4b866
	drivemap -s (hd0) ${root}
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
UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8de50eea-fb00-4bfb-8237-a46183255d80 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 266.1GB: boot/grub/core.img
 266.2GB: boot/grub/grub.cfg
 269.2GB: boot/grub/menu.lst
 266.1GB: boot/grub/stage2
 297.7GB: boot/initrd.img-2.6.31-21-generic
 267.5GB: boot/initrd.img-2.6.32-22-generic
 267.5GB: boot/vmlinuz-2.6.31-21-generic
 267.5GB: boot/vmlinuz-2.6.32-22-generic
 267.5GB: initrd.img
 297.7GB: initrd.img.old
 267.5GB: vmlinuz
 267.5GB: vmlinuz.old

Regards!
Mario Huizar

---

### Post by kansasnoob on 2010-05-07
You have more than one problem, first you installed grub2 to your Vista partition:

> sda2: __________________________________________________ _______________________

File system: ntfs
[B][COLOR="Red"]Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda2 and
looks at sector 519873518 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.[/COLOR][/B]
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe

The fix for that is detailed here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The second problem is that you have mixed legacy grub and grub2 files in the /boot/grub directory:

> sda5: __________________________________________________ _______________________

File system: ext4
Boot sector type: Grub
Boot sector info: Grub is installed in the boot sector of sda5 and looks
at sector 519873750 of the same hard drive for the
stage2 file, but no stage2 files can be found at this
location.
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/**[COLOR="Red"]menu.lst[/COLOR]** /boot/grub/**[COLOR="Red"]grub.cfg[/COLOR]** /etc/fstab
/boot/grub/core.img

To fix that we'll backup the old /boot/grub directory, create a new one, purge any configuration files and reinstall grub2:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub
```

Note: That may say, "not installed so not removed", that's OK just continue:

```
sudo apt-get --purge remove grub-pc
```

```
sudo apt-get --purge remove grub-common
```

Now we'll reinstall:

```
sudo apt-get install grub-pc
```

If, or when, asked where to install grub be sure to choose only /dev/sda and NOT a partition!

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

That should do it, but if you confront any difficulties reinstalling grub DO NOT reboot! I'll hang tight for a while in case you run into trouble.

---

### Post by mario-huizar on 2010-05-07
Hey Thanks a lot! It looks like it is working now. At least I can select the Windows entry and it goes into windows. 

The only suspicious thing is that the entry is marked as Windows Recovery Environment (loader) (on /dev/sda2). But it goes into Vista and Linux.

Thanks again!
Mario Huizar

This is my new boot info:


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 519888342 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 519873750 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1953503937 sectors.. But according to the info from 
                       the partition table , it has 1953520001 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,088   519,590,294   516,516,207   7 HPFS/NTFS
/dev/sda3         519,590,295   625,137,344   105,547,050   5 Extended
/dev/sda5         519,590,358   620,735,534   101,145,177  83 Linux
/dev/sda6         620,735,598   625,137,344     4,401,747  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B89E85849E853BBE                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        F4E8B4F6E8B4B866                       ntfs       Mario                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        05256b8a-fb03-4e43-9814-b7c698a5e8c8   ext4                                     
/dev/sda6        8de50eea-fb00-4bfb-8237-a46183255d80   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4EA1-B8DA                              vfat       Elements                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=mario)
/dev/sdb1        /media/Elements          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
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
search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 05256b8a-fb03-4e43-9814-b7c698a5e8c8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f4e8b4f6e8b4b866
	drivemap -s (hd0) ${root}
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
UUID=05256b8a-fb03-4e43-9814-b7c698a5e8c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8de50eea-fb00-4bfb-8237-a46183255d80 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 266.1GB: boot/grub/core.img
 266.2GB: boot/grub/grub.cfg
 297.7GB: boot/initrd.img-2.6.31-21-generic
 267.5GB: boot/initrd.img-2.6.32-22-generic
 267.5GB: boot/vmlinuz-2.6.31-21-generic
 267.5GB: boot/vmlinuz-2.6.32-22-generic
 267.5GB: initrd.img
 297.7GB: initrd.img.old
 267.5GB: vmlinuz
 267.5GB: vmlinuz.old

---

### Post by kansasnoob on 2010-05-07
> The only suspicious thing is that the entry is marked as Windows Recovery Environment (loader) (on /dev/sda2). But it goes into Vista and Linux.

That's somewhat typical, look at the section:

> CHANGING WINDOWS/OTHER OS TITLES

Here:

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Just be very, very careful with any editing!

---

