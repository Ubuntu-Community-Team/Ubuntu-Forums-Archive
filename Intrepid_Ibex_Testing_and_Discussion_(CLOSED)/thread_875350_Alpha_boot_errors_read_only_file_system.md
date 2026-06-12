---
title: "Alpha boot errors read only file system"
date: 2008-07-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BC7333 on 2008-07-30
Upgraded from Hardy to Intrepid Alpha2, now 3

When booting see some errors like the following:

copied manually from boot screen so possibly some typo's)

mkdir: cannot create directory '/lib/modules/2.6.26-4-generic/volatile/':read only file system

later..

setting up resolvconf...
rm: cannot remove '/etc/resolvconf/run/interface/wlan0': read only file system

/etc/rcS.d/S07resolvconf: 114: cannot create /etc/resolvconf/run/enable-updates: read only file system

Anyone know what might be the problem? launchpad bug and answers have gone unnoticed except for a confirm from another guy.

Thanks.

---

### Post by PmDematagoda on 2008-07-30
Does Ubuntu boot properly to the login screen and desktop or does it just stop through mid-boot at a terminal?

---

### Post by InfinityCircuit on 2008-07-31
What is the contents of /etc/fstab?  Is it possibe you need to fsck the disk and it is mounting it ro as a result of it not being clean?  Also, what is the LP bug #?

---

### Post by Nullack on 2008-07-31
Confirmed, boot fails with read only error, boots kernel / GDM / gnome no problem however.

---

### Post by BC7333 on 2008-08-01
> **InfinityCircuit said:**
> What is the contents of /etc/fstab?  Is it possibe you need to fsck the disk and it is mounting it ro as a result of it not being clean?  Also, what is the LP bug #?

LP bug: [https://bugs.launchpad.net/ubuntu/+bug/250189](https://bugs.launchpad.net/ubuntu/+bug/250189)

fsck has run several times.

fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7a352281-d258-4f93-ac5d-52a804db599d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=88d97d83-af6a-4443-bd1e-04a503b5e0bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```


Thanks!

---

### Post by BC7333 on 2008-08-01
> **Nullack said:**
> Confirmed, boot fails with read only error, boots kernel / GDM / gnome no problem however.

[http://ubuntuforums.org/showthread.php?t=876975](http://ubuntuforums.org/showthread.php?t=876975)

which I thought may be unrelated, but you make me think...

```
Aug  1 14:32:34 brian-laptop gdm[9522]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Aug  1 14:32:36 brian-laptop console-kit-daemon[9370]: GLib-GObject-WARNING: instance with invalid (NULL) class pointer 
Aug  1 14:32:36 brian-laptop console-kit-daemon[9370]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Aug  1 14:32:36 brian-laptop console-kit-daemon[9370]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
```

additional info:

booting sometimes sticks.. I find it helps to enter grub with esc, do e then wait a few seconds and hit b to boot.

grub.lst  albeit rather messy.. selecting generic because 'last known' does not seem to boot at all.. just black screen after a certain point.

```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu intrepid (development branch), kernel 2.6.26-ultimate
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-ultimate root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.26-ultimate
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.26-ultimate (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-ultimate root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.26-ultimate

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash  last-good-boot
initrd		/boot/last-good-boot/initrd.img
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.26-5-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.26-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.26-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-4-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.26-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.26-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-4-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.26-4-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-18-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-rt
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-18-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-18-rt

title		Ubuntu intrepid (development branch), kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-17-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-rt
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-17-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-17-rt

title		Ubuntu intrepid (development branch), kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-16-rt

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-15-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-15-rt
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-15-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-15-rt

title		Ubuntu intrepid (development branch), kernel 2.6.24-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-14-rt
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-14-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-14-rt

title		Ubuntu intrepid (development branch), kernel 2.6.24-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-14-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-12-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-12-rt
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-12-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-rt root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-12-rt

title		Ubuntu intrepid (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-11-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-11-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-10-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-10-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-10-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-10-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-8-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-8-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-8-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-8-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-5-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-5-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-5-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-5-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-5-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-4-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-4-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-4-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-2-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-2-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-2-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-2-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-2-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.24-2-generic

title		Ubuntu intrepid (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu intrepid (development branch), kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7a352281-d258-4f93-ac5d-52a804db599d ro  single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

experiencing also very intermittent screen blackouts and hang when typing and only when power is plugged in suspecting apmi.. experienced this in hardy before regularly.[https://bugs.launchpad.net/ubuntu/+bug/212514](https://bugs.launchpad.net/ubuntu/+bug/212514)  Now have acpid and apmd turned off in admin services but acpid seems to be running anyway at least at boot.  suspect something with /etc/laptop-mode/laptop-mode.conf or hotkey settings/lid switch etc.  If I close the lid on AC power it will hang.

where I did the following to try and keep the screen from turning off
```
#
# Enable laptop mode when on AC power.
#
ENABLE_LAPTOP_MODE_ON_AC=1


#
# Enable laptop mode when the laptop's lid is closed, even when we're on AC
# power? (ACPI-ONLY)
#
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=1
```

still had hangs when plugged in but the following seemed to work quite well, reducing hangs by 90 percent

/etc/default/acpi-support disabled dpmi (at least partially)

```
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false
```

and that's a wrap :)

Thanks.. know it's a lot to chew on but thought would provide the addl info to see if anyone can pick out some possible relationships.

---

### Post by BC7333 on 2008-08-01
> **PmDematagoda said:**
> Does Ubuntu boot properly to the login screen and desktop or does it just stop through mid-boot at a terminal?

Sometimes yes does boot to login (ubuntu studio) correctly, sometimes not. goes to black screen mid boot in terminal

no splash shows etc, but that's a known issue I think.

---

### Post by BC7333 on 2008-08-01
Version 2.0.20.2-0ubuntu1: 

  * If kernel headers are missing during a module build, report 
    this status properly in DKMS auto installation service. (LP: #247523)

this module now in update but have not updated yet getting 404 errs

sounds possibly related.

---

### Post by BC7333 on 2008-08-02
Problem remains even after all updates.

---

