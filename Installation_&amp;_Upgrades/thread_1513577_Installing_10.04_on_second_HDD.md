---
title: "Installing 10.04 on second HDD?"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by Rhetoric Camel on 2010-06-19
Hi I have Windows XP and Ubuntu 9.04 installed on one hard drive. I don't have much space on the drive and would like to put Ubuntu on it's own hdd, which I already have, and have files on. It's a 300gb drive, with 150gb free, I'd like to use 100gb for Ubuntu 10.04. 

How do I go about doing this without deleting my current files on my 2nd hdd. If I do this will I get a boot menu with XP, Ubuntu 9.04 and Ubuntu 10.04? Or will I have to choose to boot from that hard drive at start up? Which isn't that big of a deal to me if so.

Any help with this would be greatly appreciated!

---

### Post by darkod on 2010-06-19
If the 300GB disk has a single ntfs partition on it, you will have to shrink it first to make 100GB unallocated space. You can do this with Gparted either from the 9.04 installation or the 10.04 live mode.

Once you have the 100GB unallocated space, start the 10.04 installer and use the guided method Use Largest Available Free space to install it into the 100GB space, or just use Manual Partitioning, as you wish.

Where to install grub2 from 10.04 and where to boot from is your choice. In this situation it's probably better to install grub2 to the 300GB and make it first in boot order in BIOS. You control where grub2 is installed in the last screen of the installer, before clicking Install click on the Advanced button. If the 300GB disk is called /dev/sdb for example (it will show during step 4 when selecting where to install), tell grub2 to install on /dev/sdb.

That's it. The grub2 menu will have 10.04, 9.04 and XP.

If you can, it's best to have a backup of the data before shrinking the partition. It's usually no problem, but as with any partitioning operation, things sometimes go wrong.

---

### Post by Rhetoric Camel on 2010-06-19
Can I shrink and do that partition resizing in windows or must I be in ubuntu to do this?

---

### Post by darkod on 2010-06-19
> **Rhetoric Camel said:**
> Can I shrink and do that partition resizing in windows or must I be in ubuntu to do this?

XP doesn't have a tool for that. Since vista, you can use windows Disk Management for that, but not in XP. Your only choice is a third party windows app, or Gparted or similar linux app. You already have Gparted in ubuntu and it works quite good, so it's my choice personally.

---

### Post by Rhetoric Camel on 2010-06-19
alright will do. thanks for the help... if for any reason I need more I'll be back to ask. Thanks again

---

### Post by Rhetoric Camel on 2010-06-20
do I format to fat16 (or 32) or ext3 (or 2) for the ubuntu drive? And do I make it the primary partition, or the extended partition?

---

### Post by darkod on 2010-06-20
You have two options. Leave the space as unallocated, and just use the option Use Largest Available Free space in the installer. That will install it into the unallocated space you left. The colored bars in step 4 are showing the disk before and after the process, make sure it looks right.

Or you can create the partitions yourself with Manual Partitioning (during the install again, so no need to do anything in advance) to control the size of each, and to create separate /home partition if wanted. In that case create / and /home as ext4, swap is just swap area.

---

### Post by Rhetoric Camel on 2010-06-20
alright thank you very much I got it installed. Unfortunately I lost the load up screen that allows me to sign into ubuntu 9.04 install that I have. I would like to still be able to load into there. Is there a way I can do it possibly with a VM inside of 10.04 and load 9.04 into it?

---

### Post by darkod on 2010-06-20
You should get a grub boot menu at start offering 10.04, 9.04 and XP. Unless you had the other disk disconnected during the ubuntu install.

In that case just boot your new 10.04 and in terminal run:

sudo update-grub

---

### Post by Rhetoric Camel on 2010-06-20
I did sudo update-grub and it didn't show 9.04, just 10.04.

---

### Post by darkod on 2010-06-20
OK, lets see what you have and where. Boot the 10.04, download the boot info script in my signature, run it and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by Rhetoric Camel on 2010-06-21
after running it in terminal I get this

```
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda2/Wubi for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Finished. The results are in the file RESULTS.txt located in /home/rhetoriccamel/Desktop

```


in the .txt file I have this, is this file supposed to be this long?



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   625,137,344   522,739,035   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   411,344,324   411,344,262   7 HPFS/NTFS
/dev/sdb2         411,344,325   625,137,344   213,793,020  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       313f175a-03ba-4181-8f2d-e3f40f4599b9   ext3                                     
/dev/sda1        76C49467C4942B7F                       ntfs                                     
/dev/sda2        488CCED98CCEC124                       ntfs       For Programs                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B2E0BED6E0BE9FD1                       ntfs       Second HDD                    
/dev/sdb2        e575e192-7cce-4709-8dc3-ce2309fa8f90   ext3       Ubuntu 10.04                  
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
timeout		10

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
# kopt=root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.04, kernel 2.6.28-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: ubuntu/disks/boot/grub/menu.lst
    ??GB: ubuntu/disks/boot/initrd.img-2.6.27-14-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-15-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-18-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-19-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.27-14-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-15-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-18-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-19-generic

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro,relatime 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

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
search --no-floppy --fs-uuid --set e575e192-7cce-4709-8dc3-ce2309fa8f90
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
search --no-floppy --fs-uuid --set e575e192-7cce-4709-8dc3-ce2309fa8f90
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set e575e192-7cce-4709-8dc3-ce2309fa8f90
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 76c49467c4942b7f
	drivemap -s (hd0) ${root}
	chainloader +1
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
UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 /               ext3    errors=remount-ro 0       1
/mnt/512.swap non swap sw 0 0

=================== sdb2: Location of files loaded by Grub: ===================


 234.7GB: boot/grub/core.img
 234.7GB: boot/grub/grub.cfg
 234.6GB: boot/initrd.img-2.6.32-22-generic-pae
 234.7GB: boot/vmlinuz-2.6.32-22-generic-pae
 234.6GB: initrd.img
 234.7GB: vmlinuz
```

---

### Post by darkod on 2010-06-21
The 9.04 is a wubi install inside windows. It will not show directly in grub2.

You will have to select windows, and then the windows bootloader will show you options for XP and wubi 9.04.

---

### Post by Rhetoric Camel on 2010-06-21
> **darkod said:**
> The 9.04 is a wubi install inside windows. It will not show directly in grub2.

You will have to select windows, and then the windows bootloader will show you options for XP and wubi 9.04.

awesome thank you very much... as you can tell I haven't tried loading into windows yet. Thanks again for the help I appreciate it... had no idea I installed 9.04 on wubi.

---

