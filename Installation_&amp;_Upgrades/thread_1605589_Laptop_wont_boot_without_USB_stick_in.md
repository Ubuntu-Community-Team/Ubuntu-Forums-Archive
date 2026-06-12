---
title: "Laptop wont boot without USB stick in"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by jesushero on 2010-10-25
After several attempts at installing Ubuntu 10.10 on a Samsung N150 laptop/netbook, I have finally succeeded, but it won't boot without the installation USB drive being plugged in. 

Trying to boot it without the USB thumb drive it just stops at a black screen and does nothing. 

With the USB drive in, it doesn't actually load up the installer, as you would expect, but boots normally into Ubuntu. Once booted, you can remove the drive and it runs fine without it.

When you plug it in, it sees it as /dev/sdb, and the only hard drive is also seen as /dev/sdb. So it never mounts it. It can mount any other USB thumb drive normally.

Any pointers here? What am I doing wrong?

---

### Post by oldfred on 2010-10-25
Grub must have installed to the flash drive. Plug in flash and run this so we can see what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by jesushero on 2010-10-25
Thanks for that tip, really good tool that I wasn't aware of!

Looks like you were right, GRUB is on the flash drive.. How do I put it on the drive? 

During install, the flash drive was seen as /dev/sda and the internal drive was /dev/sdb, now has gone the other way around.

I'd rather not reinstall if possible.

Here's the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   484,571,135   484,569,088  83 Linux
/dev/sda2         484,571,136   488,396,799     3,825,664  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *  3,223,366,781 3,470,046,704   246,679,924  78 Unknown
/dev/sdb2         432,871,117 1,208,554,935   775,683,819  10 OPUS
/dev/sdb3       1,869,562,563 3,788,792,630 1,919,230,068  8b Unknown
/dev/sdb4       2,213,019,648 2,221,342,719     8,323,072   a OS/2 Boot Manager

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4
/dev/sdb4 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        758d4cb6-e645-444e-bbae-86e8182ab102   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
error: /dev/sdb1: No such file or directory
error: /dev/sdb2: No such file or directory
error: /dev/sdb3: No such file or directory
error: /dev/sdb4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
password --md5 $1$eWPEp/$1.FyfiOvc8SLU59bW7Uk2.

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
# kopt=root=UUID=758d4cb6-e645-444e-bbae-86e8182ab102 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=758d4cb6-e645-444e-bbae-86e8182ab102

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid		758d4cb6-e645-444e-bbae-86e8182ab102
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=758d4cb6-e645-444e-bbae-86e8182ab102 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid		758d4cb6-e645-444e-bbae-86e8182ab102
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=758d4cb6-e645-444e-bbae-86e8182ab102 ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		758d4cb6-e645-444e-bbae-86e8182ab102
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=758d4cb6-e645-444e-bbae-86e8182ab102 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
#UUID=2d39793d-52ca-4aa5-8671-ad0fef9f6c34 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda1: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/menu.lst
 154.7GB: boot/grub/stage2
 154.7GB: boot/initrd.img-2.6.32-25-generic
 154.7GB: boot/vmlinuz-2.6.32-25-generic
 154.7GB: initrd.img
 154.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
```

---

### Post by scottuss on 2010-10-25
Looks to me as though GRUB is indeed installed on your USB stick...

---

### Post by jesushero on 2010-10-25
OK, I think this is now solved. I installed GRUB on the drive by using the GRUB command, and telling it to install on hd0.

I restarted and it boots without the USB drive.

Thanks everyone!

Was thinking though, although I've done more than 500 installs of all versions of Ubuntu on all sorts of machines, but this was the first one on one with no CD drive. I found the installation process on this one very tricky, compared to the usual. It might be worth making it more seamless. It was very easy to not notice that GRUB was not installed on the drive. Just my feedback, in case anyone would like to look into it.

---

