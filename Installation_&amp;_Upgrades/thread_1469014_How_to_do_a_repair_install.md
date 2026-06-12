---
title: "How to do a repair install?"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by AngusM on 2010-05-01
Ok, if I can't fix my system now, then how do I do a repair install? I just downloaded the install CD, and I'm gone through the processes to do an install, but even when I manually select the mount points (/home, /, swap, and /mnt/Windoze) it says:
Directories contain system files (/etc, /lib/usr/var, ...) that already exists under any defined mountpoint will be deleted during install.

How am I supposed to just get it to boot again w/out killing all my settings and stuff?

---

### Post by VMC on 2010-05-01
What are you wanting to accomplish. To boot your system using grub?
How are you or were you able to boot before the install - Windows, grub?

We need a lot more information. Was this a recent Lucid install or upgrade?

The best advice I can give is to download boot_info_script[see my blue link below] and output the RESULTS.txt so we can see how all your partitions are tired together.

---

### Post by AngusM on 2010-05-01
> **VMC said:**
> What are you wanting to accomplish. To boot your system using grub?

Yes, that would be fine. It does seem to boot using grub, but freezes. The "repair" option that most install Linux discs offer would have been just fine, but Ubuntu 10.04 doesn't seem to have one. So what I'm trying to do is a repair install, but the install program promises to wipe out several directories, even though I've selected not to format anything.


> How are you or were you able to boot before the install - Windows, grub?

Yes, booting Ubuntu and Windows was managed by grub quite well in the past.

> We need a lot more information. Was this a recent Lucid install or upgrade?

It's not actually my computer, and the Luddites who own it claim that there wasn't anything special going on before this all happened.

> The best advice I can give is to download boot_info_script[see my blue link below] and output the RESULTS.txt so we can see how all your partitions are tired together.

All right, well this is what it had to say (running the 10.04 Live option on the install CD)
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,535,039    19,534,977  83 Linux
/dev/sda2    *     19,535,040   102,767,804    83,232,765   7 HPFS/NTFS
/dev/sda3         102,767,805   312,496,379   209,728,575   5 Extended
/dev/sda5         102,783,870   106,687,664     3,903,795  82 Linux swap / Solaris
/dev/sda6         106,687,728   312,496,379   205,808,652  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0189838d-7289-403e-a2cf-e00f67d436ec   ext3                                     
/dev/sda2        7EC41BDAC41B938D                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3b95acd3-7a77-416e-a72c-9dff7621cfda   swap                                     
/dev/sda6        5810a4ff-c5e9-4516-9330-6b051ef5eed0   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
timeout		10

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
# kopt=root=UUID=0189838d-7289-403e-a2cf-e00f67d436ec ro

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

title		Ubuntu whatever's there right now
root		(hd0,0)
kernel		/vmlinuz root=UUID=0189838d-7289-403e-a2cf-e00f67d436ec ro quiet splash
initrd		/initrd.img
quiet

title		Ubuntu whatever's there right now (recovery mode)
root		(hd0,0)
kernel		/vmlinuz root=UUID=0189838d-7289-403e-a2cf-e00f67d436ec ro single
initrd		/initrd.img

title		Winblows
root		(hd0,1)
makeactive
chainloader	+1

title		Ubuntu 10.04, memtest86+
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
UUID=0189838d-7289-403e-a2cf-e00f67d436ec /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda6
UUID=5810a4ff-c5e9-4516-9330-6b051ef5eed0 /home           ext3    defaults,relatime        0       2
# /dev/sda5
UUID=3b95acd3-7a77-416e-a72c-9dff7621cfda	none	swap	sw	0	0
#UUID=17ea293c-0959-4341-ac52-dc2d82bab4c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
#
# [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)
#usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
/dev/sda2     /mnt/c ntfs locale=en_US.utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


   8.1GB: boot/grub/menu.lst
   7.6GB: boot/grub/stage2
   7.7GB: boot/initrd.img-2.6.22-14-generic
   7.7GB: boot/initrd.img-2.6.22-14-generic.bak
   7.7GB: boot/initrd.img-2.6.24-21-generic
   7.7GB: boot/initrd.img-2.6.24-21-generic.bak
   7.8GB: boot/initrd.img-2.6.28-15-generic
   7.8GB: boot/initrd.img-2.6.28-16-generic
   8.1GB: boot/initrd.img-2.6.31-14-generic
   6.8GB: boot/initrd.img-2.6.31-15-generic
   8.1GB: boot/initrd.img-2.6.31-16-generic
   8.0GB: boot/initrd.img-2.6.31-17-generic
   9.2GB: boot/initrd.img-2.6.31-19-generic
   9.0GB: boot/initrd.img-2.6.31-20-generic
   7.8GB: boot/initrd.img-2.6.31-21-generic
   1.3GB: boot/initrd.img-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.22-14-generic
   7.7GB: boot/vmlinuz-2.6.24-21-generic
   7.8GB: boot/vmlinuz-2.6.28-15-generic
   7.6GB: boot/vmlinuz-2.6.28-16-generic
   7.8GB: boot/vmlinuz-2.6.31-14-generic
   8.1GB: boot/vmlinuz-2.6.31-15-generic
   9.1GB: boot/vmlinuz-2.6.31-16-generic
   8.5GB: boot/vmlinuz-2.6.31-17-generic
   8.2GB: boot/vmlinuz-2.6.31-19-generic
   8.1GB: boot/vmlinuz-2.6.31-20-generic
   8.8GB: boot/vmlinuz-2.6.31-21-generic
   7.8GB: boot/vmlinuz-2.6.32-21-generic
   1.3GB: initrd.img
   7.8GB: initrd.img.old
   7.8GB: vmlinuz
   8.8GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

---

### Post by tgalati4 on 2010-05-02
When you get to the partitioner, choose manual partition.  Select your appropriate mountpoints for each partition.  Be sure to UNCHECK the format box for each partition that you simply want to dist-upgrade.  This will preserve existing files and overwrite files with the exact same name.

This method can cause breakage so back up your important data regardless.

---

### Post by VMC on 2010-05-02
The RESULTS.txt file looks normal, except you have an enormous amount of kernels. You can remove some of the older ones at a later date.

One thing is your running grub-legacy. I would encourage you to upgrade to grub2.

In the mean time what happens or doesn't happen when you boot the system. What indication from grub, if any?

---

### Post by Bucky Ball on 2010-05-02
Leave the Windows partition out of the equation at the manual partitioner. Just don't touch it if you want to keep your windows install. As mentioned, untick the format box for any partitions you want to keep and JUST install Lucid to the root mountpoint /

---

### Post by AngusM on 2010-05-02
> **tgalati4 said:**
> When you get to the partitioner, choose manual partition.  Select your appropriate mountpoints for each partition.  Be sure to UNCHECK the format box for each partition that you simply want to dist-upgrade.  This will preserve existing files and overwrite files with the exact same name.

This method can cause breakage so back up your important data regardless.

I've done that: left the format box unchecked. Nevertheless, the install promises to clean out all these directories, which is what I don't want.

---

### Post by AngusM on 2010-05-02
> **VMC said:**
> The RESULTS.txt file looks normal, except you have an enormous amount of kernels. You can remove some of the older ones at a later date.

One thing is your running grub-legacy. I would encourage you to upgrade to grub2.

In the mean time what happens or doesn't happen when you boot the system. What indication from grub, if any?

Ok, I'll try upgrading to grub2, although that's rather difficult when the thing won't start anyway. I already tried talking about the boot behaviour in another forum ([http://ubuntuforums.org/showthread.php?t=1468924]("http://ubuntuforums.org/showthread.php?t=1468924")), but didn't get any joy.

---

### Post by VMC on 2010-05-02
> **AngusM said:**
> Ok, I'll try upgrading to grub2, although that's rather difficult when the thing won't start anyway. I already tried talking about the boot behaviour in another forum ([http://ubuntuforums.org/showthread.php?t=1468924]("http://ubuntuforums.org/showthread.php?t=1468924")), but didn't get any joy.

You didn't answer what happens when you boot  your system.

At any rate, boot up using livecd and then chroot into the Lucid "/" partition and follow these [instructions]("http://ubuntuforums.org/showpost.php?p=8883297&postcount=3").

Once your at a terminal, install grub2:
```
sudo apt-get install grub2
```

---

### Post by AngusM on 2010-05-02
> **VMC said:**
> You didn't answer what happens when you boot  your system.

The explanation of what happens was in that link I posted.

> 
Once your at a terminal, install grub2:
```
sudo apt-get install grub2
```

Wow! That seems to have installed an awful lot more than just grub2. I saw everything from Flash to CUPS being installed there. In any case, it seems to have worked. Now my only problem is [http://ubuntuforums.org/showthread.php?p=9221571]("http://ubuntuforums.org/showthread.php?p=9221571") and I'm too scared to proceed.

Incidentally, this appears to have happened because someone *other* than the Luddites upgraded the system (using NX!) and I'm here to pick up the pieces.

Thanks for your help

---

