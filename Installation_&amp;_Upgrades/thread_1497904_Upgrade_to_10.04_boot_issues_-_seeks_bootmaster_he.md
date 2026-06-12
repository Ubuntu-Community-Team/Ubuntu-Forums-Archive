---
title: "Upgrade to 10.04 boot issues - seeks bootmaster help!"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by CCC999 on 2010-05-31
Upgrade from Karmic - was using EasyBCD in Vista. Tried upgrading to Grub2, reinstalling Grub - but can not boot to either. Here is my Results.txt file from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/). Would appreciate any help from kindly bootmasters! Thanks..
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 169354694 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 466. But according to the info from fdisk, 
                       sdb6 starts at sector 327694336.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 2,930,272,064 2,930,272,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   163,842,047   163,840,000   7 HPFS/NTFS
/dev/sdb2         163,846,935 1,465,144,064 1,301,297,130   5 Extended
/dev/sdb5    *    163,846,998   327,693,869   163,846,872  83 Linux
/dev/sdb6         327,694,336 1,441,781,759 1,114,087,424   7 HPFS/NTFS
/dev/sdb7       1,441,785,618 1,465,144,064    23,358,447  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e435d2f2-cd32-4734-8699-4355b42de58c   ext4       Data2                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        78104CE7104CAE46                       ntfs       Vista                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        47146fb1-e580-44a5-97f0-73090840e05c   ext3       KARMIC                        
/dev/sdb6        4C78C89C78C88664                       ntfs       Data                          
/dev/sdb7        0478e3e8-43f7-420e-984a-31822b6f57ca   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Vista             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================== sdb1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD





title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet




=========================== sdb5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
timeout		 0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                     0  0  
# Entry for /dev/sda5 :
UUID=47146fb1-e580-44a5-97f0-73090840e05c  /              ext3         errors=emount-ror            0  1  
# Entry for /dev/sda6 :
UUID=4C78C89C78C88664                      /media/Data1   ntfs-3g      defaults                     0  0  
# Entry for /dev/sda1 :
UUID=78104CE7104CAE46                      /media/Vista   ntfs-3g      defaults,locale=en_US.UTF-8  0  0  
# Entry for /dev/sda7 :
UUID=0478e3e8-43f7-420e-984a-31822b6f57ca  none           swap         defaults                     0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec,utf8        0  0  

=================== sdb5: Location of files loaded by Grub: ===================


  86.7GB: boot/grub/core.img
  87.0GB: boot/grub/grub.cfg
  86.6GB: boot/grub/menu.lst
  86.7GB: boot/grub/stage2
  86.2GB: boot/initrd.img-2.6.31-14-generic
  86.0GB: boot/initrd.img-2.6.32-22-generic
  85.8GB: boot/vmlinuz-2.6.31-14-generic
  86.2GB: boot/vmlinuz-2.6.32-22-generic
  86.0GB: initrd.img
  86.2GB: vmlinuz
```

---

### Post by oldfred on 2010-05-31
You never did get grub installed to a MBR so it can boot. the easyBCD program is the one that wants other boot loaders installed to partitions so it can chainload to them. Grub2 does not like to be in a partition - they consider it less reliable.

You also have two boot flags and can only have one per drive. Use gparted right click and remove boot flag from sdb5.

You still have parts of easy in win7 I would remove this
/NST/menu.lst

The grub legacy in the sdb5 partition boot sector is ok there, just will never be used.
You need to remove the parts of grub legacy still in your /boot/grub files and install grub2 to the MBR of the drive you use to boot probably sdb. I prefer to have boot loader on same drive as operating system.

While you may be able to use the quick way to install grub2 the parts of grub legacy have been known to cause problems. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD:
Find linux partition:
sudo fdisk -l
sudo mkdir /mnt/sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

If this does not work then you will have to do the full chroot and uninstall grub legacy and reinstall grub2. I will give you a link to kansasnoob's chroot procedure if needed.

---

### Post by CCC999 on 2010-05-31
Thanks Oldfred! I'm away from my machine (work!), but will follow your suggestions this evening. Thanks for the advise!

---

### Post by CCC999 on 2010-05-31
oldfred - sorry - but still no boot. Followed your directions, ended up with a Grub prompt. I'll post a current results file. Thanks again for your assistance. 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 169354694 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 466. But according to the info from fdisk, 
                       sdb6 starts at sector 327694336.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 2,930,272,064 2,930,272,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   163,842,047   163,840,000   7 HPFS/NTFS
/dev/sdb2         163,846,935 1,465,144,064 1,301,297,130   5 Extended
/dev/sdb5         163,846,998   327,693,869   163,846,872  83 Linux
/dev/sdb6         327,694,336 1,441,781,759 1,114,087,424   7 HPFS/NTFS
/dev/sdb7       1,441,785,618 1,465,144,064    23,358,447  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e435d2f2-cd32-4734-8699-4355b42de58c   ext4       Data2                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        78104CE7104CAE46                       ntfs       Vista                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        47146fb1-e580-44a5-97f0-73090840e05c   ext3       KARMIC                        
/dev/sdb6        4C78C89C78C88664                       ntfs       Data                          
/dev/sdb7        0478e3e8-43f7-420e-984a-31822b6f57ca   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Vista             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                     0  0  
# Entry for /dev/sda5 :
UUID=47146fb1-e580-44a5-97f0-73090840e05c  /              ext3         errors=emount-ror            0  1  
# Entry for /dev/sda6 :
UUID=4C78C89C78C88664                      /media/Data1   ntfs-3g      defaults                     0  0  
# Entry for /dev/sda1 :
UUID=78104CE7104CAE46                      /media/Vista   ntfs-3g      defaults,locale=en_US.UTF-8  0  0  
# Entry for /dev/sda7 :
UUID=0478e3e8-43f7-420e-984a-31822b6f57ca  none           swap         defaults                     0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec,utf8        0  0  

=================== sdb5: Location of files loaded by Grub: ===================


  85.9GB: boot/grub/core.img
  86.2GB: boot/initrd.img-2.6.31-14-generic
  86.0GB: boot/initrd.img-2.6.32-22-generic
  85.8GB: boot/vmlinuz-2.6.31-14-generic
  86.2GB: boot/vmlinuz-2.6.32-22-generic
  86.0GB: initrd.img
  86.2GB: vmlinuz
```

---

### Post by CCC999 on 2010-05-31
oldfred - I did a search on kansasnoob's chroot procedure. Followed that, (new options became available - looked good) but still no boot. Ends back at Ubuntu logo with S and M options. Here is an up to date results - note fstab section - shows my harddrives opposite to what they should be sda vx sdb. Could this be why my boot fails?:confused: 


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 169354694 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 466. But according to the info from fdisk, 
                       sdb6 starts at sector 327694336.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 2,930,272,064 2,930,272,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   163,842,047   163,840,000   7 HPFS/NTFS
/dev/sdb2         163,846,935 1,465,144,064 1,301,297,130   5 Extended
/dev/sdb5         163,846,998   327,693,869   163,846,872  83 Linux
/dev/sdb6         327,694,336 1,441,781,759 1,114,087,424   7 HPFS/NTFS
/dev/sdb7       1,441,785,618 1,465,144,064    23,358,447  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e435d2f2-cd32-4734-8699-4355b42de58c   ext4       Data2                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        78104CE7104CAE46                       ntfs       Vista                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        47146fb1-e580-44a5-97f0-73090840e05c   ext3       KARMIC                        
/dev/sdb6        4C78C89C78C88664                       ntfs       Data                          
/dev/sdb7        0478e3e8-43f7-420e-984a-31822b6f57ca   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Vista             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                     0  0  
# Entry for /dev/sda5 :
UUID=47146fb1-e580-44a5-97f0-73090840e05c  /              ext3         errors=emount-ror            0  1  
# Entry for /dev/sda6 :
UUID=4C78C89C78C88664                      /media/Data1   ntfs-3g      defaults                     0  0  
# Entry for /dev/sda1 :
UUID=78104CE7104CAE46                      /media/Vista   ntfs-3g      defaults,locale=en_US.UTF-8  0  0  
# Entry for /dev/sda7 :
UUID=0478e3e8-43f7-420e-984a-31822b6f57ca  none           swap         defaults                     0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec,utf8        0  0  

=================== sdb5: Location of files loaded by Grub: ===================


  85.9GB: boot/grub/core.img
  85.9GB: boot/grub/grub.cfg
  86.2GB: boot/initrd.img-2.6.31-14-generic
  86.0GB: boot/initrd.img-2.6.32-22-generic
  85.8GB: boot/vmlinuz-2.6.31-14-generic
  86.2GB: boot/vmlinuz-2.6.32-22-generic
  86.0GB: initrd.img
  86.2GB: vmlinuz
```

---

### Post by oldfred on 2010-06-01
What are the S & M options. Are you booting thru grub menu ok and now into ubuntu issues perhaps the common video issues? Does recovery option work? 

The drive change does not look like it would make any difference to Ubuntu the grub.cfg has correct root and UUID. It may make a difference to Windows, but grub usually adds a switch entry that makes windows think it is first no matter what. Is there some reason the drives changed order? Is one removeable or one IDE and one SATA?

---

### Post by CCC999 on 2010-06-01
Sorry - I'm away at work and not at my PC. If I remember correctly, the S&M options refer to the first screen I see when rebooting. It has a low resolution Ubuntu with a small logo to the right, says below an error occurred while mounting /. Has options to Skip mounting (S) or do manual recovery (M). Skip produces another error message about not finding /temp, M option drops me to a prompt for ubuntu. I don't know what to try at this prompt (it is not a grub prompt - more like a terminal prompt). 
 There should be no reason for the drive change - they are both SATA, and fstab in terminal shows sdb as my boot/operating disc correctly. 
 Please let me know what you would recommend next - if nothing else, I could try installing a fresh copy on my larger hard drive...
Thanks for your assistance!

---

### Post by oldfred on 2010-06-01
I have always preferred to have a working operating system on each drive as a way to boot. If you have two drives and windows I would always suggest linux on the other drive. I have four systems on three drives. Some are just the older versions of Ubuntu, but I keep the root so I can boot the old system or look at an old setting if I need it (have not need much).

---

### Post by CCC999 on 2010-06-01
Here is a good shot of the screen I keep seeing: [http://www.alexsleat.com/2010/05/03/howto-fix-an-error-occurred-while-mounting-ubuntu-lucid-10-04/]("http://www.alexsleat.com/2010/05/03/howto-fix-an-error-occurred-while-mounting-ubuntu-lucid-10-04/") I see a slightly different message (error while mounting /).
Progress! I have both the 10.04 upgrade disc, and liveCD. Using the upgrade, I selected rescue, and the correct drives show (as I had seen before). Could not load grub anywhere, so elected to go to prompt on sdb5 (ubuntu). At the prompt tried update-grub and it seemed to work. Next boot, I get the grub menu, with correct options. However, nothing still boots - selecting Ubuntu takes me to the same screen, 'an error occurred while mounting /'.
 Researching that, it seems my etc/fstab file is totally different (corrupt) to what the results text file shows. 'sudo gedit /etc/fstab' produces
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb7 swap swap defaults 0 0
```
And I can see why grub has a problem. I only recognize the last entry. I'm thinking I should take a copy of 'sdb5/etc/fstab', perhaps modify it a bit and try that. Let me know if this is not worth trying.....

---

### Post by oldfred on 2010-06-01
Is the fstab you are seeing the one from the liveCD. You have to mount and drill down on the partition your install is on to see your fstab.

The error message you posted mentions USB. I had a time where I could not boot a year or so ago (obviously not Lucid) where if I had a USB key of something installed it would not work. As soon as I removed that it worked. Others have had issues with CD's still in tray, incorrect BIOS settings and other odd things that should not cause issues and seem to only effect a few people.

---

### Post by CCC999 on 2010-06-02
Hello oldfred - I took your advise and installed in my second HD. No issues (so far), but I would still like to be able to boot to my Vista, and previous Ubuntu install. Please take a quick look and see if you see anything I could try - Grub shows them - Vista now just reboots, and Ubuntu gives a 'error while mounting'. PS - I had a feeling that fstab was not the correct one. 

Thanks for your help.....I'll mark this closed regardless in a couple of days.....


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 169354694 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 466. But according to the info from fdisk, 
                       sdb6 starts at sector 327694336.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,539,201,929 2,539,201,867  83 Linux
/dev/sda2       2,539,202,558 2,930,276,351   391,073,794   5 Extended
/dev/sda5       2,539,202,560 2,914,332,671   375,130,112  83 Linux
/dev/sda6       2,914,334,720 2,930,276,351    15,941,632  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   163,842,047   163,840,000   7 HPFS/NTFS
/dev/sdb2         163,846,996 1,465,144,064 1,301,297,069   5 Extended
/dev/sdb5         163,846,998   327,693,869   163,846,872  83 Linux
/dev/sdb6         327,694,336 1,441,781,759 1,114,087,424   7 HPFS/NTFS
/dev/sdb7       1,441,785,618 1,465,144,064    23,358,447  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e435d2f2-cd32-4734-8699-4355b42de58c   ext4       Data2                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8f7d6ff7-d059-40a2-87a8-05916d6969a0   ext4                                     
/dev/sda6        22d9c2e9-4d4a-47e5-a7cd-cc63ae8804c1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        78104CE7104CAE46                       ntfs       Vista                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        47146fb1-e580-44a5-97f0-73090840e05c   ext3       KARMIC                        
/dev/sdb6        4C78C89C78C88664                       ntfs       Data                          
/dev/sdb7        0478e3e8-43f7-420e-984a-31822b6f57ca   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/Vista             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 8f7d6ff7-d059-40a2-87a8-05916d6969a0
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
search --no-floppy --fs-uuid --set 8f7d6ff7-d059-40a2-87a8-05916d6969a0
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
	search --no-floppy --fs-uuid --set 8f7d6ff7-d059-40a2-87a8-05916d6969a0
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8f7d6ff7-d059-40a2-87a8-05916d6969a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8f7d6ff7-d059-40a2-87a8-05916d6969a0
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8f7d6ff7-d059-40a2-87a8-05916d6969a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8f7d6ff7-d059-40a2-87a8-05916d6969a0
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=8f7d6ff7-d059-40a2-87a8-05916d6969a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8f7d6ff7-d059-40a2-87a8-05916d6969a0
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=8f7d6ff7-d059-40a2-87a8-05916d6969a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8f7d6ff7-d059-40a2-87a8-05916d6969a0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8f7d6ff7-d059-40a2-87a8-05916d6969a0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 78104ce7104cae46
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro single
	initrd /boot/initrd.img-2.6.31-14-generic
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
UUID=8f7d6ff7-d059-40a2-87a8-05916d6969a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=22d9c2e9-4d4a-47e5-a7cd-cc63ae8804c1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


1416.1GB: boot/grub/core.img
1347.7GB: boot/grub/grub.cfg
1416.1GB: boot/initrd.img-2.6.32-21-generic
1416.3GB: boot/initrd.img-2.6.32-22-generic
1416.1GB: boot/vmlinuz-2.6.32-21-generic
1300.3GB: boot/vmlinuz-2.6.32-22-generic
1416.3GB: initrd.img
1416.1GB: initrd.img.old
1300.3GB: vmlinuz
1416.1GB: vmlinuz.old

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=47146fb1-e580-44a5-97f0-73090840e05c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 47146fb1-e580-44a5-97f0-73090840e05c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 78104ce7104cae46
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                     0  0  
# Entry for /dev/sda5 :
UUID=47146fb1-e580-44a5-97f0-73090840e05c  /              ext3         errors=emount-ror            0  1  
# Entry for /dev/sda6 :
UUID=4C78C89C78C88664                      /media/Data1   ntfs-3g      defaults                     0  0  
# Entry for /dev/sda1 :
UUID=78104CE7104CAE46                      /media/Vista   ntfs-3g      defaults,locale=en_US.UTF-8  0  0  
# Entry for /dev/sda7 :
UUID=0478e3e8-43f7-420e-984a-31822b6f57ca  none           swap         defaults                     0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec,utf8        0  0  

=================== sdb5: Location of files loaded by Grub: ===================


  86.0GB: boot/grub/core.img
  86.0GB: boot/grub/grub.cfg
  86.2GB: boot/initrd.img-2.6.31-14-generic
  86.0GB: boot/initrd.img-2.6.32-22-generic
  85.8GB: boot/vmlinuz-2.6.31-14-generic
  86.2GB: boot/vmlinuz-2.6.32-22-generic
  86.0GB: initrd.img
  86.2GB: vmlinuz
```

---

### Post by oldfred on 2010-06-02
For Vista I would try two things. One, I usually see a drivemap entry added by the osprober when windows is not on the first drive (actually I see it most of the time but it is just mapping 0 to root which is the same.) Maybe Vista does not need it??

gksudo gedit /etc/grub.d/40_custom
add this & then run the sudo update-grub:

menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 78104CE7104CAE46
    drivemap -s (hd1) ${root}
    chainloader +1
}

Sometimes windows just need repairs. this is a list of the repairs but it may be fixboot or rebuild BCD? Do not run fixMBR unless you want to put the windows bootloader in the MBR.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors 
BootRec.exe /FixBoot  #updates PBR partition boot sector 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by CCC999 on 2010-06-10
thanks oldfred. I'll mark this solved as it turns out I likely had a hardware failure complicating my upgrade to 10.04. Per your recommendation, ran chkdsk on the original boot HDD. Next reboot that drive no longer worked. I had backups of my essential files. Just recently I converted from windows Quicken to Moneydance - and that application has a super backup system. Haven't gotten around to installing windows yet....(might be a while!). Thanks again for your assistance!

---

### Post by oldfred on 2010-06-10
Quicken is still the only reason I boot XP several times a week. I am starting to use Kmymoney and trying GnuCash. How is Moneydance?

My problem really is my quicken goes back to DOS, to win3.1, win95, win98 & now winXP, so I have a lot of history even with purges of some old history.

---

