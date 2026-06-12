---
title: "Upgraded from 8.04LTS 10.04.1LTS , now I can't boot."
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by CptanPanic on 2010-08-28
I just upgraded my server, and now I am stuck at "Kernel panic- not synching: VFS: Unable to mount root fs on unknown-block(0,0)"  I have read other suggestions about booting to previous kernels to reinstall latest kernel, but that doesn't work since I can't boot to any kernel.  How can I fix this with the restore cd or from grub2 command line.  Reinstalling is not an option as I have lots of configurations that I don't want to lose.
Thanks,
CP

---

### Post by oldfred on 2010-08-28
As part of the upgrade did you say not to install the maintainer's version of grub's menu.lst? Then you are booting the old kernel in the new system and have to manually update it.

To  see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by CptanPanic on 2010-08-28
There was an error at the end of upgrade, and it did not complete so it may have skipped something.   But the menu.lst is showing new kernels.  Thanks for the quick reply and hopefully data below will show you something.   

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   970,711,559   970,711,497  83 Linux
/dev/sda2         970,711,560   976,768,064     6,056,505   5 Extended
/dev/sda5         970,711,623   976,768,064     6,056,442  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a2ee2642-6929-4932-9eeb-53e483022f6f   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1cdc68de-ee62-42d9-b56a-b9a6278ff8f2   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        22d3f484-b613-4290-9053-59b2ac777f55   ext3                                     
/dev/sdb: PTTYPE="dos" 

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
# kopt=root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro quiet splash
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro single

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-28-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro quiet splash
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a2ee2642-6929-4932-9eeb-53e483022f6f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 10.04.1 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=a2ee2642-6929-4932-9eeb-53e483022f6f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=1cdc68de-ee62-42d9-b56a-b9a6278ff8f2 none            swap    sw              0       0
#/dev/sdd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb3 	/mnt/oldroot  	reiserfs relatime			 0       1
/dev/sdb1 	/mnt/oldboot  	ext2	 noauto,relatime,errors=remount-ro 0       1
/dev/sdc1 	/mnt/backup 	ext3	 relatime,errors=remount-ro 0       1
/dev/sdd1 	/mnt/mybook  	ext3	 relatime,errors=remount-ro 0       1
#/dev/sde1 	/mnt/mybook  	ext3	 relatime,errors=remount-ro 0       1


=================== sda1: Location of files loaded by Grub: ===================


  76.0GB: boot/grub/menu.lst
  75.9GB: boot/grub/stage2
  74.8GB: boot/initrd.img-2.6.24-19-generic
  74.8GB: boot/initrd.img-2.6.24-19-generic.bak
  74.9GB: boot/initrd.img-2.6.24-23-generic
  74.9GB: boot/initrd.img-2.6.24-23-generic.bak
  76.0GB: boot/initrd.img-2.6.24-24-generic
  74.9GB: boot/initrd.img-2.6.24-24-generic.bak
  74.9GB: boot/initrd.img-2.6.24-25-generic
  74.9GB: boot/initrd.img-2.6.24-25-generic.bak
 188.9GB: boot/initrd.img-2.6.24-26-generic
 188.9GB: boot/initrd.img-2.6.24-26-generic.bak
 188.9GB: boot/initrd.img-2.6.24-27-generic
 188.9GB: boot/initrd.img-2.6.24-27-generic.bak
 188.8GB: boot/initrd.img-2.6.24-28-generic
 188.9GB: boot/initrd.img-2.6.24-28-generic.bak
  76.1GB: boot/initrd.img-2.6.32-24-generic
  74.7GB: boot/vmlinuz-2.6.24-19-generic
 188.8GB: boot/vmlinuz-2.6.24-23-generic
  74.9GB: boot/vmlinuz-2.6.24-24-generic
  74.8GB: boot/vmlinuz-2.6.24-25-generic
  74.9GB: boot/vmlinuz-2.6.24-26-generic
 188.9GB: boot/vmlinuz-2.6.24-27-generic
 188.9GB: boot/vmlinuz-2.6.24-28-generic
 188.9GB: boot/vmlinuz-2.6.32-24-generic
  76.1GB: initrd.img
 188.8GB: initrd.img.old
 188.9GB: vmlinuz
 188.9GB: vmlinuz.old

```

---

### Post by oldfred on 2010-08-28
I do not see anything, not sure about kernel panics.

Grub/Ubuntu do not use boot flags, but some BIOS need a flag. But that is not related.

You have lots of kernels, most now from old system. You may want to houseclean and or limit the number of kernels shown in menu.lst when you can get back into your system.
## e.g. howmany=all
##      howmany=7
# howmany=2

The best I can suggest someone else may have a better solution is to chroot into your system and run full updates to refresh it, but that may just be where you are at?

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

Then run a full set of updates:
Commands once in chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by CptanPanic on 2010-08-28
I tried all the above and no difference.  I also tried going into synaptic and reinstalling linux-image and grub, but to no avail.  Any other ideas?  Is there no way to just use the live cd to boot directly into my old install?  What else can I try?
Thanks

---

### Post by CptanPanic on 2010-08-28
I was able to get it to work by installing grub2.  Not sure what got messed up, but I can boot now.

---

