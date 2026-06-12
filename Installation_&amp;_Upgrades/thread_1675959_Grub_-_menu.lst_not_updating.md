---
title: "Grub - menu.lst not updating"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by Qu4rk on 2011-01-26
A while back, I commented out all the old entries in my menu.lst with a "#" so that when I look at the boot screen it doesn't have an infinite list of old kernels to load that I never load.  Well, I just noticed that the newest kernel from the update is not running.  I'm still running .24 kernel.  How do I resolve this issue so that:

1) I'm running the correct kernel from todays update.

2) I prevent this from happening in the future.

Thanks

---

### Post by oldos2er on 2011-01-26
Which version of Ubuntu are you running? Since you appear to be using legacy grub, there's a program called Startupmanager that makes it easy to configure your menu.lst. [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by kansasnoob on 2011-01-26
In order to answer your question we should see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Qu4rk on 2011-01-26
Here you go:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

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

/dev/sda1    *             63   167,734,664   167,734,602   7 HPFS/NTFS
/dev/sda2         167,734,665   625,137,344   457,402,680   5 Extended
/dev/sda5         167,734,728   606,999,959   439,265,232  83 Linux
/dev/sda6         607,000,023   625,137,344    18,137,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        205813DD5813B110                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b02e8d44-8787-4e6f-b407-2dc003b138b0   ext3                                     
/dev/sda6        1d724ae7-ab93-4b99-8c12-b3e7b53b1825   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b02e8d44-8787-4e6f-b407-2dc003b138b0

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-23-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-23-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-22-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-22-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-21-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-21-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.31-20-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.31-20-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1d724ae7-ab93-4b99-8c12-b3e7b53b1825 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 129.9GB: boot/grub/menu.lst
 127.5GB: boot/grub/stage2
 127.5GB: boot/initrd.img-2.6.28-11-generic
 127.5GB: boot/initrd.img-2.6.31-20-generic
 127.5GB: boot/initrd.img-2.6.32-21-generic
 127.5GB: boot/initrd.img-2.6.32-22-generic
 128.1GB: boot/initrd.img-2.6.32-23-generic
 183.8GB: boot/initrd.img-2.6.32-24-generic
 187.1GB: boot/initrd.img-2.6.32-25-generic
 197.3GB: boot/initrd.img-2.6.32-26-generic
 200.1GB: boot/initrd.img-2.6.32-27-generic
 233.7GB: boot/initrd.img-2.6.32-28-generic
 127.5GB: boot/vmlinuz-2.6.28-11-generic
 127.5GB: boot/vmlinuz-2.6.31-20-generic
 127.5GB: boot/vmlinuz-2.6.32-21-generic
 127.6GB: boot/vmlinuz-2.6.32-22-generic
 128.1GB: boot/vmlinuz-2.6.32-23-generic
 179.5GB: boot/vmlinuz-2.6.32-24-generic
 129.0GB: boot/vmlinuz-2.6.32-25-generic
 129.2GB: boot/vmlinuz-2.6.32-26-generic
 182.8GB: boot/vmlinuz-2.6.32-27-generic
 230.2GB: boot/vmlinuz-2.6.32-28-generic
 233.7GB: initrd.img
 200.1GB: initrd.img.old
 230.2GB: vmlinuz
 182.8GB: vmlinuz.old
```

---

### Post by kansasnoob on 2011-01-27
Sorry to take so long, this is the first opportunity I've had to look.

I think instead of commenting out those entries you should have changed the **[COLOR="Red"]all[/COLOR]** shown below to a **[COLOR="Red"]1[/COLOR]** (That's a "one"):

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=**[COLOR="Red"]all[/COLOR]**
```

So try removing the comments you added, changing the "all" to "1", and then running:

```
sudo update-grub
```

As oldos2er said you can in the future select how many kernels to display using the Advanced tab in Startup Manager:

[https://help.ubuntu.com/community/StartUpManager?action=AttachFile&do=get&target=sum-advanced.png](https://help.ubuntu.com/community/StartUpManager?action=AttachFile&do=get&target=sum-advanced.png)

But I think adding those comments in the "automagic" section breaks the ability for legacy grub to update properly.

---

### Post by presence1960 on 2011-01-27
Another cause may be when you installed the new kernel were you presented with an option to choose which version of GRUB menu.lst to use? If you were you should choose "use package maintainer version". If you choose one of the other options the new kernel is not added to menu.lst and may need to be added manually.

---

### Post by Qu4rk on 2011-01-27
This didn't work.  I uncommented what I commented, did a grub update & I'm still running .24.  And I downloaded startupmanager & it only gives me up to .24 kernel.  Any other suggestions?

> **kansasnoob said:**
> Sorry to take so long, this is the first opportunity I've had to look.

I think instead of commenting out those entries you should have changed the **[COLOR="Red"]all[/COLOR]** shown below to a **[COLOR="Red"]1[/COLOR]** (That's a "one"):

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=**[COLOR="Red"]all[/COLOR]**
```

So try removing the comments you added, changing the "all" to "1", and then running:

```
sudo update-grub
```

As oldos2er said you can in the future select how many kernels to display using the Advanced tab in Startup Manager:

[https://help.ubuntu.com/community/StartUpManager?action=AttachFile&do=get&target=sum-advanced.png](https://help.ubuntu.com/community/StartUpManager?action=AttachFile&do=get&target=sum-advanced.png)

But I think adding those comments in the "automagic" section breaks the ability for legacy grub to update properly.

I was never presented with any of this.

> **presence1960 said:**
> Another cause may be when you installed the new kernel were you presented with an option to choose which version of GRUB menu.lst to use? If you were you should choose "use package maintainer version". If you choose one of the other options the new kernel is not added to menu.lst and may need to be added manually.

---

### Post by presence1960 on 2011-01-27
Look in Synaptic Package Manager to see if the kernel you think is missing is indeed installed. Look under linux-headers-x.x.xx-xx and linux-image-x.x.xx-xx

If it is indeed installed you will manually need to add the entries for that kernel in menu.lst

Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```Add the red below and make sure you swap xx for the kernel #. Just make sure the complete kernel # matches what you insert in menu.lst

```
## ## End Default Options ##
[COLOR="Red"]title		Ubuntu 10.04.1 LTS, kernel 2.6.32-xx-generic
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-xx-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-xx-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-xx-generic (recovery mode)
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-xx-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
initrd		/boot/initrd.img-2.6.32-xx-generic[/COLOR]



title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-23-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-23-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-22-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-22-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-21-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-21-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.31-20-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.31-20-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Click save and close the file. Reboot. You should have the new kernel in GRUB menu. If it is indeed installed properly you will be able to boot to it.

---

### Post by presence1960 on 2011-01-27
To get rid of all those kernels you don't use go to Synaptic Package Manager and mark for Removal or Complete Removal the older kernels these items:

linux-headers-x.x.xx-xx
linux-image-x.x.xx-xx

Mark for Removal uninstalls the packages but leaves them in cache. mark for complete removal uninstalls the packages and removes them from cache so you would have to download them again if you ever decided to reinstall them. With kernels you will usually not want to reinstall them.

This will clean up your GRUB menu.

---

### Post by Qu4rk on 2011-01-27
This worked!  Thanks man!

> **presence1960 said:**
> Look in Synaptic Package Manager to see if the kernel you think is missing is indeed installed. Look under linux-headers-x.x.xx-xx and linux-image-x.x.xx-xx

If it is indeed installed you will manually need to add the entries for that kernel in menu.lst

Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```Add the red below and make sure you swap xx for the kernel #. Just make sure the complete kernel # matches what you insert in menu.lst

```
## ## End Default Options ##
[COLOR="Red"]title		Ubuntu 10.04.1 LTS, kernel 2.6.32-xx-generic
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-xx-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-xx-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-xx-generic (recovery mode)
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-xx-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
initrd		/boot/initrd.img-2.6.32-xx-generic[/COLOR]



title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-23-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-23-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-22-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-22-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-21-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.32-21-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.31-20-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.31-20-generic

#title		Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic (recovery mode)
#uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b02e8d44-8787-4e6f-b407-2dc003b138b0 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		b02e8d44-8787-4e6f-b407-2dc003b138b0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Click save and close the file. Reboot. You should have the new kernel in GRUB menu. If it is indeed installed properly you will be able to boot to it.

---

### Post by Qu4rk on 2011-01-27
Startup Manager is perfect for this!

Thanks again!

> **presence1960 said:**
> To get rid of all those kernels you don't use go to Synaptic Package Manager and mark for Removal or Complete Removal the older kernels these items:

linux-headers-x.x.xx-xx
linux-image-x.x.xx-xx

Mark for Removal uninstalls the packages but leaves them in cache. mark for complete removal uninstalls the packages and removes them from cache so you would have to download them again if you ever decided to reinstall them. With kernels you will usually not want to reinstall them.

This will clean up your GRUB menu.

---

### Post by presence1960 on 2011-01-27
> **Qu4rk said:**
> This worked!  Thanks man!

You are welcome, enjoy Ubuntu.

---

### Post by shailendrak on 2011-06-11
Hi,
My /etc/sudoers file got corrupted as i changed it.

I am not able to see grub menu on restart after pressing shift key.

How do I restore sudoers files

I am using ubuntu 10.04.1 LTS

Please Help

---

