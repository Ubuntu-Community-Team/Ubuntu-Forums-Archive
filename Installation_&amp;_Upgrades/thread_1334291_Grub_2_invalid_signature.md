---
title: "Grub 2 invalid signature"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by ltlbgr67 on 2009-11-22
Ok, heres what happened.  Weeks ago was running 1 win xp, and 2 ubuntu on 1 hd, and on second hd was running win xp.
This is my menu list for that setup

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
# kopt=root=UUID=09b92bb9-b26a-44af-abe0-38cda98b0df7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=09b92bb9-b26a-44af-abe0-38cda98b0df7

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

title		Ubuntu 8.10,  server kernel 2.6.27-11-generic
uuid		09b92bb9-b26a-44af-abe0-38cda98b0df7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=09b92bb9-b26a-44af-abe0-38cda98b0df7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		09b92bb9-b26a-44af-abe0-38cda98b0df7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=09b92bb9-b26a-44af-abe0-38cda98b0df7 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		09b92bb9-b26a-44af-abe0-38cda98b0df7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=09b92bb9-b26a-44af-abe0-38cda98b0df7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		09b92bb9-b26a-44af-abe0-38cda98b0df7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=09b92bb9-b26a-44af-abe0-38cda98b0df7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		09b92bb9-b26a-44af-abe0-38cda98b0df7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=09b92bb9-b26a-44af-abe0-38cda98b0df7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		09b92bb9-b26a-44af-abe0-38cda98b0df7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=09b92bb9-b26a-44af-abe0-38cda98b0df7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		09b92bb9-b26a-44af-abe0-38cda98b0df7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title       Windows XP Old Ver
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Freespire 2.0 (2.0) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=/dev/sda5 
initrd		/boot/initrd.img-2.6.20-16-lowlatency
savedefault
boot

When ubuntu 9.1 cam out tried updating one of my 9.04 and thats when it crapped out.  Got the blinking screen ect.  Got my windows on hd0 to boot and decided I would do clean install of Ubuntu 9.1.  I couldnt remember which partition had the Ubuntu that was now gooded up so I was going to delete my ubuntus and install new.  My 2nd hd has some important info so I thought I would disconnect it while goofing with installing the 9.10

Got everything to work on the 1st hard drive fine and hooked up the second hard drive with just vista on it.  Not realizing I now had grub2 i was tryikng to find menu.lst....   Figured out I had grub 2 and read some post on sudo update-grub.

It found the xp on the second hard drive but when selecting that drive to boot it gives me Error: Invalid signature   Pressing any key gets me back to grub.

Current grub.cfg reads

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ddcb9f2e-453e-4a0e-b246-31502681060b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ddcb9f2e-453e-4a0e-b246-31502681060b ro single 
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
	search --no-floppy --fs-uuid --set 01c97ad000eba800
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.#
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
set root=(hd0,2)
search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe#
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
set root=(hd0,2)
search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ddcb9f2e-453e-4a0e-b246-31502681060b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ddcb9f2e-453e-4a0e-b246-31502681060b ro single 
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
	search --no-floppy --fs-uuid --set 01c97ad000eba800
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


### END /etc/grub.d/40_custom ###
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ddcb9f2e-453e-4a0e-b246-31502681060b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set ddcb9f2e-453e-4a0e-b246-31502681060b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ddcb9f2e-453e-4a0e-b246-31502681060b ro single 
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
	search --no-floppy --fs-uuid --set 01c97ad000eba800
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


### END /etc/grub.d/40_custom ###


### END /etc/grub.d/40_custom ###

Any help on how to get this to also boot xp off the second drive would be appreciated.

---

### Post by namok on 2009-11-24
[Follow this link]("http://ubuntuforums.org/showthread.php?t=1291280") and to next post attach file RESULTS.TXT.

---

### Post by ltlbgr67 on 2009-11-24
Here are the results you asked for.  Hopefully I attached them correctly.

---

### Post by oldfred on 2009-11-25
I would first rerun the sudo update-grub. I am surprised it only has part of your windows boot stanza for sdb1.

If that does not work try adding this to /etc/grub.d/40_custom and then run sudo update-grub to add it to grub.cfg

menuentry "Windows XP on sdb1" {
       insmod ntfs
       set root=(hd1,1)
       search --no-floppy --fs-uuid --set 08947F49947F37F0
       drivemap -s (hd1) (hd0)
       chainloader +1
}

---

### Post by ltlbgr67 on 2009-11-25
Ok, I marked it as solved in so far as it now works.

My next question would be if it is possible to remove the windows entry that is created from the scripts that does not work.  Also, how about when it updates and puts a new version of linux on the loader?

Here is my new grub.cfg

---

### Post by ltlbgr67 on 2009-11-25
Thank you both nomak and oldfred.  You are what makes Ubuntu so fun to use and learn.

---

### Post by oldfred on 2009-11-26
You can turn off the osprober either by making it non-executable or in grub file add a command. If you ever change other systems you may have to turn the prober back on or manually add entries. As long as you edited one of the executable files starting with two digits and an underscore that file is inicluded in every update of grub.cfg. So if you edited 40_custom it will always be included.

/etc/default/grub 
GRUB_DISABLE_OS_PROBER=true

---

