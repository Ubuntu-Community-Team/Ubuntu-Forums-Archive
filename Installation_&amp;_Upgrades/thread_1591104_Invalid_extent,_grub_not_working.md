---
title: "Invalid extent, grub not working"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by kiwited on 2010-10-08
I am trying to install 10.10 on a Seagate 500GB external USB drive without success.
1. Install from CD. Froze at Time Zone part. Workaround was to "Try Ubuntu" and install from there, which seemed to work fine.
2. After install, the drive will not boot. I get a flashing cursor for a while then the message "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key..."
3. Then various errors depending on what I have tried - eg "error: invalid extent" followed by grub rescue or unable to find kernel or even the disk sometimes.
4. The only command that seems to work in grub rescue is "ls" which gives (hd0) (hd0,msdos1)
5. I reboot on my normal drive (Ubuntu 10.04) with the USB drive attached, and run "update-grub" - the USB drive appears in grub.cfg.
6. I reboot and select the 10.10 from the grub menu
7. error messages appear.
"error: invalid extent"
"error: you need to load the kernel first.
press any key to continue..."
8. Pressing a key then dumps me back into the grub menu.

The Seagate hard drive is new, and works fine as a storage medium. I have tried to install from two different machines, both running 10.04, and there is no problem with access to the drive from another drive. I have now installed at least five times, and have reinstalled grub twice in addition, but cannot get this drive to boot.

Help please!!

Theo

---

### Post by psusi on 2010-10-08
1)  Make sure your bios has the sata controller set to AHCI mode, not IDE emulation mode.

2)  On the livecd, open System->Administration->Disk Utility and run the long SMART test on the drive and make sure it doesn't have any errors.

---

### Post by kiwited on 2010-10-08
Thanks for the answer.

It made no difference changing the SATA controller except for a message about the CDROM flashing up too fast to read.

The disk checked out OK.

I have also tried to install onto a similar, but 1TB, disk with unusual results. I used EXT3 instead of EXT4, but had the same outcome as the other drive.

I then updated grup and rebooted, this time trying to access the new filesystem. After a delay, it booted into the new system. I then rebooted to try and access the earlier one, again without success.

Back to the new one and it was inaccessible, with the same error messages as the other.

Could it be that you cannot use an external USB hard drive?

Theo

---

### Post by psusi on 2010-10-08
How large of a disk is this?  It could be that your bios is buggy and can't access that large of a disk.

Can you run the bootinfo script from the livedc and post the output?

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by drs305 on 2010-10-08
> 4. The only command that seems to work in grub rescue is "ls" which gives (hd0) (hd0,msdos1)

Did you happen to try to install Grub2 on your Windows partition. I've seen this message when that was attempted.

If you can boot a LiveCD please download and run the boot info script from here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by kiwited on 2010-10-08
The script text is attached. Hope this helps.

Many thanks, Theo

---

### Post by drs305 on 2010-10-08
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

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

/dev/sda1               4,094    40,964,095    40,960,002   5 Extended
/dev/sda5               4,096    40,964,095    40,960,000  82 Linux swap / Solaris
/dev/sda2         321,669,495   625,137,344   303,467,850  83 Linux
/dev/sda3    *     40,965,750    81,931,499    40,965,750  83 Linux
/dev/sda4          81,931,500   321,669,494   239,737,995  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   973,707,263   973,705,216  83 Linux
/dev/sdc2         973,709,310   976,773,119     3,063,810   5 Extended
/dev/sdc5         973,709,312   976,773,119     3,063,808  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        5cfb8378-3130-4461-9624-0ff02278dfbe   ext3       Ubuntu Hardy LTS              
/dev/sda3        ce747f52-0e40-4a44-a21a-ff5d1300426c   ext3                                     
/dev/sda4        f9fef795-f4c7-4eaa-8338-27881cb0e34a   ext4                                     
/dev/sda5        405a477d-e612-4a2b-851b-9d87dc606160   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        98694609-fe3d-449e-b9cc-782b564eab7d   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        a92c686c-f60b-47ad-a4a1-53d28c23e957   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/98694609-fe3d-449e-b9cc-782b564eab7d ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5cfb8378-3130-4461-9624-0ff02278dfbe /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 170.4GB: boot/grub/menu.lst
 242.9GB: boot/grub/stage2
 306.8GB: boot/initrd.img-2.6.24-26-generic
 301.4GB: boot/initrd.img-2.6.24-26-generic.bak
 301.4GB: boot/initrd.img-2.6.24-27-generic
 301.4GB: boot/initrd.img-2.6.24-27-generic.bak
 289.4GB: boot/vmlinuz-2.6.24-26-generic
 300.6GB: boot/vmlinuz-2.6.24-27-generic
 301.4GB: initrd.img
 306.8GB: initrd.img.old
 300.6GB: vmlinuz
 289.4GB: vmlinuz.old

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ce747f52-0e40-4a44-a21a-ff5d1300426c /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  21.2GB: boot/grub/stage2
  22.1GB: boot/initrd.img-2.6.27-9-generic
  21.6GB: boot/initrd.img-2.6.28-15-generic
  22.1GB: boot/initrd.img-2.6.32-14-generic
  25.4GB: boot/initrd.img-2.6.32-15-generic
  21.5GB: boot/vmlinuz-2.6.27-9-generic
  21.6GB: boot/vmlinuz-2.6.28-15-generic
  21.8GB: boot/vmlinuz-2.6.32-14-generic
  21.6GB: boot/vmlinuz-2.6.32-15-generic
  25.4GB: initrd.img
  22.1GB: initrd.img.old
  21.6GB: vmlinuz
  21.8GB: vmlinuz.old


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro splash vga=771  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	echo	'Loading Linux 2.6.32-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro single splash vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro splash vga=771  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro single splash vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro splash vga=771  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	echo	'Loading Linux 2.6.32-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro single splash vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro splash vga=771  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro single splash vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro splash vga=771  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=f9fef795-f4c7-4eaa-8338-27881cb0e34a ro single splash vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set f9fef795-f4c7-4eaa-8338-27881cb0e34a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5cfb8378-3130-4461-9624-0ff02278dfbe
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro quiet splash
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5cfb8378-3130-4461-9624-0ff02278dfbe
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro single
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5cfb8378-3130-4461-9624-0ff02278dfbe
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro quiet splash
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5cfb8378-3130-4461-9624-0ff02278dfbe
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=5cfb8378-3130-4461-9624-0ff02278dfbe ro single
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.4 LTS, memtest86+ (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5cfb8378-3130-4461-9624-0ff02278dfbe
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu lucid (development branch) (10.04) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce747f52-0e40-4a44-a21a-ff5d1300426c
	linux /boot/vmlinuz-2.6.27-9-generic root=/dev/sda3
	initrd /boot/initrd.img-2.6.27-9-generic
}
menuentry "Ubuntu lucid (development branch) (10.04) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce747f52-0e40-4a44-a21a-ff5d1300426c
	linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sda3
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu lucid (development branch) (10.04) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce747f52-0e40-4a44-a21a-ff5d1300426c
	linux /boot/vmlinuz-2.6.32-14-generic root=/dev/sda3
	initrd /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu lucid (development branch) (10.04) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce747f52-0e40-4a44-a21a-ff5d1300426c
	linux /boot/vmlinuz-2.6.32-15-generic root=/dev/sda3
	initrd /boot/initrd.img-2.6.32-15-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb2)" {
	insmod ext2
	set root='(/dev/sdb,2)'
	search --no-floppy --fs-uuid --set 00899f9c-347a-4d1a-a000-caf90134d595
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=00899f9c-347a-4d1a-a000-caf90134d595 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root='(/dev/sdb,2)'
	search --no-floppy --fs-uuid --set 00899f9c-347a-4d1a-a000-caf90134d595
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=00899f9c-347a-4d1a-a000-caf90134d595 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc1)" {
	insmod ext2
	set root='(/dev/sdc,1)'
	search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=98694609-fe3d-449e-b9cc-782b564eab7d ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root='(/dev/sdc,1)'
	search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=98694609-fe3d-449e-b9cc-782b564eab7d ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=405a477d-e612-4a2b-851b-9d87dc606160 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


  72.1GB: boot/grub/core.img
 141.3GB: boot/grub/grub.cfg
  72.3GB: boot/initrd.img-2.6.32-21-generic-pae
  74.1GB: boot/initrd.img-2.6.32-22-generic-pae
  72.3GB: boot/initrd.img-2.6.32-23-generic-pae
  72.4GB: boot/initrd.img-2.6.32-24-generic-pae
  72.4GB: boot/initrd.img-2.6.32-25-generic-pae
  72.2GB: boot/vmlinuz-2.6.32-21-generic-pae
  73.1GB: boot/vmlinuz-2.6.32-22-generic-pae
  72.3GB: boot/vmlinuz-2.6.32-23-generic-pae
  72.2GB: boot/vmlinuz-2.6.32-24-generic-pae
  72.3GB: boot/vmlinuz-2.6.32-25-generic-pae
  72.4GB: initrd.img
  72.4GB: initrd.img.old
  72.3GB: vmlinuz
  72.2GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=98694609-fe3d-449e-b9cc-782b564eab7d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=98694609-fe3d-449e-b9cc-782b564eab7d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=98694609-fe3d-449e-b9cc-782b564eab7d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a92c686c-f60b-47ad-a4a1-53d28c23e957 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 311.5GB: boot/grub/core.img
 311.5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
 311.5GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
 311.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

Note: Code tags generated by pressing the **#** icon in the post's menubar.

---

### Post by drs305 on 2010-10-08
I've looked through your file and would like you to add your 10.10 entry to a 40_custom file. I won't be online much longer but have time to offer this without extended troubleshooting.

You can boot normally to 10.04, so boot to the Desktop and we will make a custom entry (/etc/grub.d/40_custom) which will appear at the bottom of the Grub2 menu.

```
gksu gedit /etc/grub.d/40_custom
```

Add the following below the existing 4-6 lines of text (below whatever currently exists):

> 


menuentry "Ubuntu Test 10.10, 2.6.35-22-generic (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 98694609-fe3d-449e-b9cc-782b564eab7d
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=98694609-fe3d-449e-b9cc-782b564eab7d ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}



Save the file, then update Grub2:
```
sudo update-grub
```

Reboot and select the last entry: "Ubuntu Test 10.10, 2.6.35-22-generic (on /dev/sdc1)"

---

### Post by kiwited on 2010-10-09
Have done this:-
1. Big delay in booting - hung before grub with message about CD-ROM medium. Cold reboot another brief delay then grub menu.
2. Same as before:
"error: invalid extent"
"error: you need to load the kernel first.
press any key to continue..."
 3. Pressing a key then dumps me back into the grub menu.

Thanks for your help

Theo

---

### Post by drs305 on 2010-10-09
In your original post you wrote:
> 
5. I reboot on my normal drive (Ubuntu 10.04) with the USB drive attached, and run "update-grub" - the USB drive appears in grub.cfg.


I understood that to mean that your system booted normally as long as you selected Ubuntu 10.04 - even with the USB connected.

Is that correct, or were you experiencing long delays and problems even booting to your 10.04 installation?

---

### Post by kiwited on 2010-10-09
The delay regarding CD-ROM only appeared after changing the SATA emulation. There has always been something of a delay when the external drive was plugged in. Without the external drive booting is very fast.

The exercise at the moment comes about through trying to install Ubuntu on a drive that is similar to my 1TB drive for a foreign student staying with us for a few days who wants to take this back to Germany with him.

I had not previously tried to put an OS onto this drive, although I have successfully put Ubuntu onto flash drives and my net book.

Theo

---

### Post by psusi on 2010-10-09
Did you try checking the filesystem?  sudo e2fsck -f /dev/sdxx

---

### Post by kiwited on 2010-10-09
Thanks for your patience.

I have done a filesystem check:

theo@theo-desktop:~$ sudo e2fsck -f /dev/sdb2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb2: 131492/6340608 files (0.1% non-contiguous), 733015/25340529 blocks

The check was done on my drive, which is showing the same behaviour.

Theo

---

