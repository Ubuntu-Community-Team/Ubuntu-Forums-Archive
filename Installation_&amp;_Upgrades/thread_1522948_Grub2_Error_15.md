---
title: "Grub2 Error 15"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by rlmcclain on 2010-07-02
I'm running an upgraded 10.04 32bit with and upgraded to grub2 installation. Everything has been fine. Yesterday I updated the system with a group of patches including the a linux upgrade to 2.6.32-23, which requested a reboot. Upon reboot, I received numerous error and X would not start (using a nvidia driver). It appeared that the system was booting using the old grub with a very outdated menu.lst file. I attempted to reinstall / reconfigure grub2 and ended up now with Error 15: file not found. I found this thread and [https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15). I did the steps outlined in the wiki to no avail - still getting the Error 15. Below is the output of the boot_info_script. The report says that core.img is not found. But it is in /boot/grub. I'm at a loss. Any help would be appreciated.

Rich

Boot Info Script 0.55 dated February 15th, 2010 

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #1 for /boot/grub.
=> Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________ _______________________

File system: ext3
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 and 
looks at sector 54247519 of the same hard drive for 
core.img, but core.img can not be found at this 
location.
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
/boot/grub/core.img

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info: 

sda5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

sda3: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 

sdb1: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 63 61,432,559 61,432,497 83 Linux
/dev/sda2 157,099,635 160,071,659 2,972,025 5 Extended
/dev/sda5 157,099,698 160,071,659 2,971,962 82 Linux swap / Solaris
/dev/sda3 61,432,560 157,099,634 95,667,075 83 Linux


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 63 390,716,864 390,716,802 83 Linux


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL 

/dev/loop0 squashfs 
/dev/sda1 d11e0a43-8551-47b9-8bea-d379685d0da4 ext3 
/dev/sda2: PTTYPE="dos" 
/dev/sda3 5a8ae9cf-f4ba-4785-8770-e6c9b6b47cfe ext3 
/dev/sda5 75cb0b2f-3494-4d37-ab71-5012629f4532 swap 
/dev/sda: PTTYPE="dos" 
/dev/sdb1 f7acbbc0-ccc2-4da8-99f2-0d904b4f5d3c ext3 
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sda1 /mnt ext3 (rw)
/dev /mnt/dev none (rw,bind)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title	 Windows 95/98/NT/2000
# root	 (hd0,0)
# makeactive
# chainloader	+1
#
# title	 Linux
# root	 (hd0,1)
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title	 Chainload into GRUB 2
root	 (hd0,0)
kernel	 /boot/grub/core.img

title	 ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title	 When you have verified GRUB 2 works, you can use this command to
root

title	 complete the upgrade: upgrade-from-grub-legacy
root

title	 ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title	 Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.32-23-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	 /boot/initrd.img-2.6.32-23-generic
quiet

title	 Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.32-23-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single
initrd	 /boot/initrd.img-2.6.32-23-generic

title	 Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.32-22-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	 /boot/initrd.img-2.6.32-22-generic
quiet

title	 Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.32-22-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single
initrd	 /boot/initrd.img-2.6.32-22-generic

title	 Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.31-17-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	 /boot/initrd.img-2.6.31-17-generic
quiet

title	 Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.31-17-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single
initrd	 /boot/initrd.img-2.6.31-17-generic

title	 Ubuntu 10.04 LTS, kernel 2.6.28-17-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.28-17-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	 /boot/initrd.img-2.6.28-17-generic
quiet

title	 Ubuntu 10.04 LTS, kernel 2.6.28-17-generic (recovery mode)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.28-17-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single
initrd	 /boot/initrd.img-2.6.28-17-generic

title	 Ubuntu 10.04 LTS, kernel 2.6.27-11-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.27-11-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	 /boot/initrd.img-2.6.27-11-generic
quiet

title	 Ubuntu 10.04 LTS, kernel 2.6.27-11-generic (recovery mode)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.27-11-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single
initrd	 /boot/initrd.img-2.6.27-11-generic

title	 Ubuntu 10.04 LTS, kernel 2.6.22-15-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.22-15-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	 /boot/initrd.img-2.6.22-15-generic
quiet

title	 Ubuntu 10.04 LTS, kernel 2.6.22-15-generic (recovery mode)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.22-15-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single
initrd	 /boot/initrd.img-2.6.22-15-generic

title	 Ubuntu 10.04 LTS, memtest86+
root	 (hd0,0)
kernel	 /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
echo	'Loading Linux 2.6.32-23-generic ...'
linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single 
echo	'Loading initial ramdisk ...'
initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
echo	'Loading Linux 2.6.32-22-generic ...'
linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single 
echo	'Loading initial ramdisk ...'
initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
echo	'Loading Linux 2.6.31-17-generic ...'
linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single 
echo	'Loading initial ramdisk ...'
initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
linux	/boot/vmlinuz-2.6.28-17-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	/boot/initrd.img-2.6.28-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
echo	'Loading Linux 2.6.28-17-generic ...'
linux	/boot/vmlinuz-2.6.28-17-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single 
echo	'Loading initial ramdisk ...'
initrd	/boot/initrd.img-2.6.28-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
linux	/boot/vmlinuz-2.6.27-11-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	/boot/initrd.img-2.6.27-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
echo	'Loading Linux 2.6.27-11-generic ...'
linux	/boot/vmlinuz-2.6.27-11-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single 
echo	'Loading initial ramdisk ...'
initrd	/boot/initrd.img-2.6.27-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.22-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
linux	/boot/vmlinuz-2.6.22-15-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro quiet splash
initrd	/boot/initrd.img-2.6.22-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.22-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
echo	'Loading Linux 2.6.22-15-generic ...'
linux	/boot/vmlinuz-2.6.22-15-generic root=UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 ro single 
echo	'Loading initial ramdisk ...'
initrd	/boot/initrd.img-2.6.22-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d11e0a43-8551-47b9-8bea-d379685d0da4
linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=d11e0a43-8551-47b9-8bea-d379685d0da4 / ext3 defaults,errors=remount-ro,relatime 0 1
# /dev/sda1
UUID=f7acbbc0-ccc2-4da8-99f2-0d904b4f5d3c /home ext3 defaults,relatime 0 2
# /dev/sdb5
UUID=75cb0b2f-3494-4d37-ab71-5012629f4532 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
//192.168.11.8/share /mnt/kurobox cifs user=rich,password=rlmtux,uid=1000,gid=1000 0 0

=================== sda1: Location of files loaded by Grub: ===================


27.7GB: boot/grub/core.img
27.7GB: boot/grub/grub.cfg
27.6GB: boot/grub/menu.lst
7.0GB: boot/initrd.img-2.6.22-15-generic
6.9GB: boot/initrd.img-2.6.22-15-generic.bak
27.6GB: boot/initrd.img-2.6.27-11-generic
27.6GB: boot/initrd.img-2.6.28-17-generic
27.6GB: boot/initrd.img-2.6.31-17-generic
27.7GB: boot/initrd.img-2.6.32-22-generic
27.6GB: boot/initrd.img-2.6.32-23-generic
1.3GB: boot/vmlinuz-2.6.22-15-generic
27.7GB: boot/vmlinuz-2.6.27-11-generic
27.7GB: boot/vmlinuz-2.6.28-17-generic
27.7GB: boot/vmlinuz-2.6.31-17-generic
27.7GB: boot/vmlinuz-2.6.32-22-generic
27.6GB: boot/vmlinuz-2.6.32-23-generic
27.6GB: initrd.img
27.7GB: initrd.img.old
27.6GB: vmlinuz
27.7GB: vmlinuz.old

---

### Post by rlmcclain on 2010-07-02
As you can see in the previous post. I have to disk. An 80Gb disk containing / and a 200Gb disk conaining /home. I just noticed something after booting into a live-cd a couple of times. Sometimes, the 80Gb disk is recognized as sda and the 200Gb as sdb, sometimes the reverse. Seems like this could be contributing to the grub2 booting problems.

Rich

---

### Post by darkod on 2010-07-02
Did you finish off the grub2 upgrade process by running upgrade-from-grub-legacy as it says to do?

---

### Post by SoFl W on 2010-07-02
If you put that text inside "code" tags it wont take up so much space.  The code tag is located in the format panel above the text box under "#"

If you searched for "err15" you would have come across a few threads on this topic.  Follow [**THIS**]("https://wiki.ubuntu.com/Grub2#Err15")

---

### Post by rlmcclain on 2010-07-02
Thanks for the advice on using code tags. I've haven't posted much. Usually I can fix my problem by reading what's already on the forum. But not this time.

I've searched for and read many posts on Error 15 including the one you pointed to. I've run all the commands, including the update-from-grub-legacy and installed grub2 on /dev/sda (when it was mounted as /). 

This issue I just posted about is that sometimes the drive containing the / partition is recognized on boot as /dev/sda and sometimes as /dev/sdb. 

/boot/grub/grub.cfg says:
set root='(hd0,1)'
linux /boot/vmlinuz-2-6.32-23-generic root-UUID=d11e0a43(..etc)

I just booted into the live-cd and sudo blkid shows this:
/dev/sda1: UUID='f7acbbc0(..etc)
/dev/sdb1: UUID='d11e0a43(..etc)
which is the reverse of grub.cfg.

Rich

---

### Post by rlmcclain on 2010-07-02
While researching the sda/sdb order issue, I found an entry in the bios from my system board that allowed me to set the Hard Disk Boot Priority. It was set to 1) the 200Gb disk (containing /home), 2) the 80Gb disk (containing /). I reversed the settings. And was able to boot successfully without getting the Error 15. I haven't changed this setting before today since building the system a couple of years ago. And my boot problems only started after the 2.6.32-23 upgrade. Odd, but solved for now.

Rich

---

