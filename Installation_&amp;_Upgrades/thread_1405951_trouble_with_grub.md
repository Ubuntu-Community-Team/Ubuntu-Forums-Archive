---
title: "trouble with grub"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by brijraj22 on 2010-02-13
i had installed the karmic koala on my portable hdd and installed the grub loader on the portable hdd. it was working fine until yesterday, but since yesterday when i boot up my laptop from the portable hdd,the grub screen shows and then everything goes black (the machine shuts down) if i select to log into ubuntu.it works fine if there i select and log into the windows option (installed on the laptop's hdd). is there a way to repair it?

if not, how can i retrieve my data from the portable hdd.i tried booting from the ubuntu cd and copying my stuff from the portable hdd to the laptop's hdd but it says that i cannot perform any file operations as im not the owner. how do i solve that problem?

any help would be greatly appreciated

---

### Post by darkod on 2010-02-13
Look at the instructions I've posted in post #2 here:
[http://ubuntuforums.org/showthread.php?t=1405953](http://ubuntuforums.org/showthread.php?t=1405953)

and post your results.txt file content here.

---

### Post by brijraj22 on 2010-02-13
can u elaborate it a bit plz. im totally clueless when it comes to doing something in ubuntu

---

### Post by darkod on 2010-02-13
The post #2 there has the explanation. You download the script, move it on desktop and execute it in terminal (Applications-Accessories) with the command given there.

---

### Post by brijraj22 on 2010-03-09
"
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1328775 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x705f705f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,975,199    40,975,137   7 HPFS/NTFS
/dev/sda2          40,975,200   312,575,759   271,600,560   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c932c92

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   150,336,269   150,336,207  83 Linux
/dev/sdb2         150,336,270   156,296,384     5,960,115   5 Extended
/dev/sdb5         150,336,333   156,296,384     5,960,052  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6C40021C4001EE20                       ntfs                                     
/dev/sda2        40A4C6E0A4C6D794                       ntfs       Data                          
/dev/sdb1        1777a88d-f454-4cf4-98e7-2801760cbbb1   ext4                                     
/dev/sdb5        7c0dec25-d818-4b2b-95a3-fa59673ef70e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/6C40021C4001EE20  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/1777a88d-f454-4cf4-98e7-2801760cbbb1 ext4       (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1777a88d-f454-4cf4-98e7-2801760cbbb1

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		1777a88d-f454-4cf4-98e7-2801760cbbb1
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		1777a88d-f454-4cf4-98e7-2801760cbbb1
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		1777a88d-f454-4cf4-98e7-2801760cbbb1
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		1777a88d-f454-4cf4-98e7-2801760cbbb1
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		1777a88d-f454-4cf4-98e7-2801760cbbb1
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		1777a88d-f454-4cf4-98e7-2801760cbbb1
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		1777a88d-f454-4cf4-98e7-2801760cbbb1
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		1777a88d-f454-4cf4-98e7-2801760cbbb1
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 1777a88d-f454-4cf4-98e7-2801760cbbb1
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1777a88d-f454-4cf4-98e7-2801760cbbb1
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1777a88d-f454-4cf4-98e7-2801760cbbb1
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1777a88d-f454-4cf4-98e7-2801760cbbb1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1777a88d-f454-4cf4-98e7-2801760cbbb1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6c40021c4001ee20
	drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=1777a88d-f454-4cf4-98e7-2801760cbbb1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=7c0dec25-d818-4b2b-95a3-fa59673ef70e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/core.img
    .7GB: boot/grub/grub.cfg
   1.5GB: boot/grub/menu.lst
    .5GB: boot/initrd.img-2.6.31-14-generic
    .7GB: boot/initrd.img-2.6.31-15-generic
   1.5GB: boot/initrd.img-2.6.31-16-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: boot/vmlinuz-2.6.31-15-generic
    .8GB: boot/vmlinuz-2.6.31-16-generic
   1.5GB: initrd.img
    .7GB: initrd.img.old
    .8GB: vmlinuz
    .2GB: vmlinuz.old
"

---

### Post by audiomick on 2010-03-09
I can't see anything there that I know is wrong. The only thing is here
```
sdb1: __________________________________________________  _______________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1328775 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/[COLOR=Red]menu.lst[/COLOR] /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img
```That looks like you have relics of a grub legacy as well as the grub 2 that the boot info script found. I don't know if this will cause problems, though.

There rest of it actually looks correct to me, but I am a long way from being good at reading the output to that script.

Just keep watching the thread. Now that you have posted the results.txt, I think you should get a response. If no-one has answered by tomorrow or so, just bump the thread (make a new post on the thread. Most people just write a post with "bump" in it)

You might want to add code tags around that output to make it easier to read. If you select "edit" in the post, then click on "go advanced" at the bottom of the edit window that opens. Select all of the text from the results.txt file, then click on the # symbol at the top of the window.

Sorry I can't help more than that.

---

