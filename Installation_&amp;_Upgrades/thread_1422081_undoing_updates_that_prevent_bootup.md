---
title: "undoing updates that prevent bootup"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2010-03-05
I just installed 9.10 on a separate drive in my system.  The update manager told me many updates were required, so I went ahead and installed.  It needed to restart, but the system just got stuck after the default GRUB entry started loading.

Is there a way to undo the updates?  I can't boot into 9.10 any more so I'm not sure how this would work.

Thanks
Mike

---

### Post by lidex on 2010-03-05
So you have dual-boot with jaunty and karmic, correct? If you can boot into jaunty, do so and click on the boot-info script link in my sig. Follow the instructions there and post the results back to this thread. If you can't boot your install, use the LiveCD.

---

### Post by 5circles on 2010-03-05
> **lidex said:**
> So you have dual-boot with jaunty and karmic, correct? If you can boot into jaunty, do so and click on the boot-info script link in my sig. Follow the instructions there and post the results back to this thread. If you can't boot your install, use the LiveCD.

Jaunty and Karmic, yes.  There is also 8.04 - that reappeared in the options at some point, and is on a second partition on the first disk.  I upgraded to GRUB2 as it seemed easier than continuing to work with GRUB Legacy.

Here is the output from the script:
Thanks!
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=ffc950e3-0151-4d5f-9d33-603312990851)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e26bf

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   477,178,694   477,178,632  83 Linux
/dev/sda2         958,566,420   976,768,064    18,201,645   5 Extended
/dev/sda5         958,566,483   976,768,064    18,201,582  82 Linux swap / Solaris
/dev/sda3         477,178,695   954,357,389   477,178,695  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb08360fc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   976,768,064   976,768,064  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007d0fe

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   607,048,154   607,048,092  83 Linux
/dev/sdc2         607,048,155   625,137,344    18,089,190   5 Extended
/dev/sdc5         607,048,218   625,137,344    18,089,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2eb4df38-c683-4930-9de1-0f79c45cd680   ext3       sda1                          
/dev/sda3        cd676c4d-b068-46c3-83a9-286de06db2e2   ext3       sda3                          
/dev/sda5        70695ca6-7581-4bb8-8e50-831ffb173e89   swap                                     
/dev/sdb1        3158e44b-7568-4627-9b3a-258239378a0a   ext2       Maxtor500                     
/dev/sdc1        ffc950e3-0151-4d5f-9d33-603312990851   ext4                                     
/dev/sdc5        a8e6a0d4-71af-4872-9a87-7a1177d85d7a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdc1        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default         0

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
# kopt=root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2eb4df38-c683-4930-9de1-0f79c45cd680

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
##      altoptions=(single-user) single
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

title		Chainload into GRUB 2
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Debian GNU/Linux, kernel 2.6.28-18-generic
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
initrd		/boot/initrd.img-2.6.28-18-generic

title		Debian GNU/Linux, kernel 2.6.28-18-generic (recovery mode)
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Debian GNU/Linux, kernel 2.6.28-17-generic
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
initrd		/boot/initrd.img-2.6.28-17-generic

title		Debian GNU/Linux, kernel 2.6.28-17-generic (recovery mode)
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Debian GNU/Linux, kernel 2.6.28-16-generic
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
initrd		/boot/initrd.img-2.6.28-16-generic

title		Debian GNU/Linux, kernel 2.6.28-16-generic (recovery mode)
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Debian GNU/Linux, kernel 2.6.28-15-generic
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic

title		Debian GNU/Linux, kernel 2.6.28-15-generic (recovery mode)
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		2eb4df38-c683-4930-9de1-0f79c45cd680
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,1)
search --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,1)
search --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
menuentry "Ubuntu, linux 2.6.28-18-generic" {
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-18-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single 
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-17-generic" {
	linux	/boot/vmlinuz-2.6.28-17-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, linux 2.6.28-17-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-17-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single 
	initrd	/boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic" {
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic" {
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic" {
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (on /dev/sda3) (recovery mode) (on /dev/sda3)" {
	set root=(hd0,3)
	linux /boot/vmlinuz-2.6.24-24-generic root=UUID=cd676c4d-b068-46c3-83a9-286de06db2e2 ro single
	initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda3)" {
	set root=(hd0,3)
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=70695ca6-7581-4bb8-8e50-831ffb173e89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//networkstorage/public\040disk\0402 /mnt/NAS200   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//ardmore/vista /mnt/ardmore smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0


=================== sda1: Location of files loaded by Grub: ===================


 118.9GB: boot/grub/core.img
 118.9GB: boot/grub/grub.cfg
 119.0GB: boot/grub/menu.lst
 118.9GB: boot/initrd.img-2.6.28-11-generic
 118.9GB: boot/initrd.img-2.6.28-15-generic
 118.9GB: boot/initrd.img-2.6.28-16-generic
 119.0GB: boot/initrd.img-2.6.28-17-generic
 118.9GB: boot/initrd.img-2.6.28-18-generic
 119.0GB: boot/vmlinuz-2.6.28-11-generic
 119.0GB: boot/vmlinuz-2.6.28-15-generic
 118.9GB: boot/vmlinuz-2.6.28-16-generic
 119.0GB: boot/vmlinuz-2.6.28-17-generic
 119.0GB: boot/vmlinuz-2.6.28-18-generic
 118.9GB: initrd.img
 119.0GB: initrd.img.old
 119.0GB: vmlinuz
 119.0GB: vmlinuz.old

=========================== sda3/boot/grub/menu.lst: ===========================

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
default		4

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
# kopt=root=UUID=cd676c4d-b068-46c3-83a9-286de06db2e2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=cd676c4d-b068-46c3-83a9-286de06db2e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (on /dev/sda3) (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=cd676c4d-b068-46c3-83a9-286de06db2e2 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cd676c4d-b068-46c3-83a9-286de06db2e2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=70695ca6-7581-4bb8-8e50-831ffb173e89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 383.7GB: boot/grub/menu.lst
 383.6GB: boot/grub/stage2
 383.7GB: boot/initrd.img-2.6.24-16-generic
 383.6GB: boot/initrd.img-2.6.24-16-generic.bak
 383.6GB: boot/initrd.img-2.6.24-24-generic
 383.7GB: boot/initrd.img-2.6.24-24-generic.bak
 383.6GB: boot/vmlinuz-2.6.24-16-generic
 383.6GB: boot/vmlinuz-2.6.24-24-generic
 383.6GB: initrd.img
 383.7GB: initrd.img.old
 383.6GB: vmlinuz
 383.6GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-20-generic root=/dev/sdg1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-20-generic root=/dev/sdg1 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdg1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdg1 ro single 
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
menuentry "Ubuntu, linux 2.6.28-18-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-18-generic (single-user mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-17-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, linux 2.6.28-17-generic (single-user mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic (single-user mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic (single-user mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2eb4df38-c683-4930-9de1-0f79c45cd680 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Memory test (memtest86+) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/memtest86+.bin 
}
menuentry "Memory test (memtest86+, serial console 115200) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb4df38-c683-4930-9de1-0f79c45cd680
	linux /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (on /dev/sda3) (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cd676c4d-b068-46c3-83a9-286de06db2e2
	linux /boot/vmlinuz-2.6.24-24-generic root=UUID=cd676c4d-b068-46c3-83a9-286de06db2e2 ro single
	initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cd676c4d-b068-46c3-83a9-286de06db2e2
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=ffc950e3-0151-4d5f-9d33-603312990851 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=a8e6a0d4-71af-4872-9a87-7a1177d85d7a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  12.1GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .8GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .7GB: boot/vmlinuz-2.6.31-20-generic
    .8GB: initrd.img
    .5GB: initrd.img.old
    .7GB: vmlinuz
    .5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by 5circles on 2010-03-05
I don't know what exactly I did - perhaps nothing and it was just that the first reboot needed to take longer, combined with the other issues I'm seeing.  Anyway, I'm up and running enough to use the applications I needed temporarily - so I can do a clean reinstall shortly.  Hopefully some of the remaining issues will go away with a clean install:    
   GRUB Loading shows up for about a minute
   Grub stanza text doesn't display properly
   Grub-update shows lots of errors

Thanks
Mike

---

### Post by presence1960 on 2010-03-05
You may not be able to boot Ubuntu 9.10 because you are missing /boot/grub/core.img
See my 9.10 info from my boot info script below:

```
sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab [COLOR="Red"]/boot/grub/core.img[/COLOR]
```

Now here is yours:

```
sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    [COLOR="DarkRed"]Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab[/COLOR]

```

---

### Post by 5circles on 2010-03-05
Thanks presence1960.  The instructions you posted earlier - since disappeared from the forum - seemed complete and easy to follow.  But I wasn't able to make them work.  I suspect that's because I provided incomplete information.  The drive that I'm using for 9.10 is an external USB drive.  I think there is some virtualization or device swapping going on because this drive sometimes seems to be /dev/sdc and sometimes /dev/sdg.  I tried the instructions with both sdg and sdc, but I think things are in a knot.

I'm thinking that the best plan is probably to start over with just the internal drives.  Now that I've figured out how to reinstall my applications with up-to-date data that shouldn't be too hard, and hopefully it will solve some of the other issues, such as not rebooting reliably.

---

### Post by presence1960 on 2010-03-05
> **5circles said:**
> Thanks presence1960.  The instructions you posted earlier - since disappeared from the forum - seemed complete and easy to follow.  But I wasn't able to make them work.  I suspect that's because I provided incomplete information.  The drive that I'm using for 9.10 is an external USB drive.  I think there is some virtualization or device swapping going on because this drive sometimes seems to be /dev/sdc and sometimes /dev/sdg.  I tried the instructions with both sdg and sdc, but I think things are in a knot.

I'm thinking that the best plan is probably to start over with just the internal drives.  Now that I've figured out how to reinstall my applications with up-to-date data that shouldn't be too hard, and hopefully it will solve some of the other issues, such as not rebooting reliably.
I removed those instructions because after I posted them I then noticed you were missing files necessary to boot 9.10- thus the post you now see.

---

