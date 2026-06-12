---
title: "Another poor soul with grub trouble"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by St Stephen on 2010-03-28
installed win7 and then reinstalled grub only to have the grub shell come up when I startup.  When I use the boot command it says there are no loaded kernels and when I use root (hd0,4) it says the file system does not exist.  Anyone have any idea's? I ran the boot info script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   146,882,294   146,882,232   7 HPFS/NTFS
/dev/sda2         146,882,295   195,366,464    48,484,170   5 Extended
/dev/sda5         146,882,358   193,261,949    46,379,592  83 Linux
/dev/sda6         193,262,013   195,366,464     2,104,452  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        34202C58202C237A                       ntfs                                     
/dev/sda5        a4a7fb00-1c55-4506-ac27-544a7e3f240f   ext3                                     
/dev/sda6        eb3adc36-b68b-456e-9e11-9071ccc0717b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/a4a7fb00-1c55-4506-ac27-544a7e3f240f ext3       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a4a7fb00-1c55-4506-ac27-544a7e3f240f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=a4a7fb00-1c55-4506-ac27-544a7e3f240f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=a4a7fb00-1c55-4506-ac27-544a7e3f240f ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=a4a7fb00-1c55-4506-ac27-544a7e3f240f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=a4a7fb00-1c55-4506-ac27-544a7e3f240f ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=a4a7fb00-1c55-4506-ac27-544a7e3f240f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=a4a7fb00-1c55-4506-ac27-544a7e3f240f ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=a4a7fb00-1c55-4506-ac27-544a7e3f240f / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=eb3adc36-b68b-456e-9e11-9071ccc0717b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/IBM_PRELOAD ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


  94.5GB: boot/grub/core.img
  85.5GB: boot/grub/menu.lst
  85.4GB: boot/grub/stage2
  75.5GB: boot/initrd.img-2.6.31-16-generic
  85.5GB: boot/initrd.img-2.6.31-17-generic
  97.6GB: boot/initrd.img-2.6.31-20-generic
  85.5GB: boot/vmlinuz-2.6.31-16-generic
  80.0GB: boot/vmlinuz-2.6.31-17-generic
  86.9GB: boot/vmlinuz-2.6.31-20-generic
  97.6GB: initrd.img
  85.5GB: initrd.img.old
  86.9GB: vmlinuz
  80.0GB: vmlinuz.old
```

btw I'm running 9.10
thanks in advance!

---

### Post by mikewhatever on 2010-03-28
I was wondering, which live cd did you use to reinstall Grub? Was it 9.10?

---

### Post by St Stephen on 2010-03-29
yeah it was the 9.10 livecd

---

### Post by oldfred on 2010-03-29
But I bet you did a upgrade to 9.10 from 9.04 so you really had old grub legacy (0.97).

You show grub2 in the MBR and menu.lst from old grub in the partition and no grub.cfg? You have to uninstall one of the two grubs as it gets confused when both are partially installed.

Lets see if just a full reinstall of grub2 works.

While in the LiveCD, open terminal and run:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by St Stephen on 2010-03-29
Well now it seems like grub can at least see my partitions, but it still boots to the grub shell and says there are no loaded kernels.  I also mounted proc dev and sys to use update-grub to create grub.cfg.  Im not really intimately familiar with grub so maybe im missing something simple.

---

### Post by St Stephen on 2010-03-29
anyone have any suggestions?

---

### Post by oldfred on 2010-03-29
If you still have parts of grub legacy and grub2, it still creates problems. I would make sure to uninstall grub & grub2 and reinstall grub2 (grub-pc) from the liveCD and chroot into your system:

Of course you must first know what partition you want to mount, in this example I'm using sda5 (# is comment):

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
apt-get update
apt-get update && sudo apt-get upgrade  #this updates everything
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
apt-get purge grub grub-pc grub-common #deletes both grub & grub2
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common  # reinstalls grub2
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

```

---

### Post by St Stephen on 2010-03-29
well grub is unistalled now, but I cant reinstall it.  when I apt-get install grub-pc grub-common I get "Could not resolve us.archive.ubuntu.com"
I cant ping anything when im chrooted but it works fine from the livecd; i switched to wired to see if that would help but there was no change.

---

### Post by oldfred on 2010-03-29
Did you include this line, which may be required for connnection?

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

---

### Post by St Stephen on 2010-03-29
that did it! after a grub-install and grub-update everything's running fine again.  Thanks for the help!

---

### Post by oldfred on 2010-03-30
Glad you got it working.;)

---

