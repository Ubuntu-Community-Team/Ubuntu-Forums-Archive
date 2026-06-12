---
title: "After upgrade, can't boot 10.10"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by sekkitsune on 2010-11-12
Quick summary:

I had a working 10.04 installation, and I decided to upgrade to 10.10 (via the command line, I tend to not use this box as a desktop, though it isn't a Server install or anything). Rebooted, and it showed an error of the sort "udevd-work[xxx]: opening directory /dev/null failed: no such file or directory", and then it went to black. Pinging the box suggested that it wasn't doing anything but sitting there, half-dead.

I booted from a 10.04 LiveCD I had handy, and tried to debug, checking the boot settings. Here's the output of Boot Info Script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2JTransneptune
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   614,502,314   614,502,252  83 Linux
/dev/sda2         614,502,315   625,137,344    10,635,030   5 Extended
/dev/sda5         614,502,378   625,137,344    10,634,967  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         577,713,465   586,099,394     8,385,930  83 Linux
/dev/sdb2         575,608,950   577,713,464     2,104,515  83 Linux
/dev/sdb3                  63   575,608,949   575,608,887  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1e71625b-3729-404e-a872-be52f74f464f   ext3       Root                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        73e278bc-b8e8-4f64-902a-db8d90e47e8b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        86c9ae60-9b8e-43e0-9bc1-1c61d595a0d9   ext3       WWW                           
/dev/sdb2        51859bc6-8984-4683-a052-f599a4ae130d   ext3       MySQL                         
/dev/sdb3        5f646f13-8731-4edb-ac8a-f6d8505131c0   ext3       Home                          
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext3       (rw)
/dev             /mnt/dev                 none       (rw,bind)
/dev/pts         /mnt/dev/pts             none       (rw,bind)


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
# kopt=root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro

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
# defoptions=quiet splash noapic

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

title		Ubuntu 10.10, kernel 2.6.35-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.10, kernel 2.6.32-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.10, kernel 2.6.32-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.10, kernel 2.6.32-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.10, kernel 2.6.31-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.10, kernel 2.6.28-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 10.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 10.10, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1e71625b-3729-404e-a872-be52f74f464f ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1e71625b-3729-404e-a872-be52f74f464f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=73e278bc-b8e8-4f64-902a-db8d90e47e8b none            swap    sw              0       0
UUID=5f646f13-8731-4edb-ac8a-f6d8505131c0	/home	ext3	rw,nodev,relatime	0	0
UUID=51859bc6-8984-4683-a052-f599a4ae130d	/var/lib/mysql	ext3	rw,nodev,relatime	0	0
UUID=86c9ae60-9b8e-43e0-9bc1-1c61d595a0d9	/var/www	ext3	rw,nodev,relatime	0	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.4GB: boot/grub/menu.lst
  21.5GB: boot/grub/stage2
  21.5GB: boot/initrd.img-2.6.24-22-generic
  21.5GB: boot/initrd.img-2.6.24-22-generic.bak
  21.5GB: boot/initrd.img-2.6.27-11-generic
  21.6GB: boot/initrd.img-2.6.28-16-generic
  21.6GB: boot/initrd.img-2.6.31-22-generic
  21.6GB: boot/initrd.img-2.6.32-22-generic
  21.5GB: boot/initrd.img-2.6.32-23-generic
  21.5GB: boot/initrd.img-2.6.32-24-generic
  21.5GB: boot/initrd.img-2.6.32-25-generic
  21.5GB: boot/initrd.img-2.6.35-22-generic
  21.4GB: boot/vmlinuz-2.6.24-22-generic
  72.2GB: boot/vmlinuz-2.6.27-11-generic
  45.4GB: boot/vmlinuz-2.6.28-16-generic
  45.4GB: boot/vmlinuz-2.6.31-22-generic
  45.3GB: boot/vmlinuz-2.6.32-22-generic
  45.4GB: boot/vmlinuz-2.6.32-23-generic
  21.5GB: boot/vmlinuz-2.6.32-24-generic
  21.6GB: boot/vmlinuz-2.6.32-25-generic
  21.5GB: boot/vmlinuz-2.6.35-22-generic
  21.5GB: initrd.img
  21.5GB: initrd.img.old
  21.5GB: vmlinuz
  21.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

And now I'm left with no further ideas. I made a 10.10 LiveCD, too, and tried to use that, with no luck&#8212;the same black screen.

Edit: Just noticed that the date on the Boot Info Script is horribly wrong; didn't bother to correct the time settings in the LiveCD instance.

---

### Post by sekkitsune on 2010-11-12
The issue seems resolved, though I'm not sure what I did. I'm treading on eggshells now, but at least I have a login. Time to try to diagnose.

---

