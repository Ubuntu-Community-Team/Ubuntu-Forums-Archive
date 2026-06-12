---
title: "Failed upgrade from Karma to Lucid"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by red oak on 2010-06-16
Attempted an upgrade through an Update Manager.

It failed, I followed instructions for sending a bug report and I was informed that my system might not be usable.

I followed the advise in other threads:

apt-get clean
apt-get autoclean
apt-get autoremove

Here I got some errors:

> Searching for GRUB installation directory ... found: /boot/grub
/etc/default/grub: line 1: default: command not found
User postinst hook script [/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
E: Sub-process /usr/bin/dpkg returned an error code (1)


sudo apt-get update
sudo apt-get install -f
 
More errors:

> Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
/etc/default/grub: line 1: default: command not found
User postinst hook script [/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.32-22-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


gconf-cleaner

The program 'gconf-cleaner' is currently not installed.  You can install it by typing:
sudo apt-get install gconf-cleaner


That's about it for now.  I did not install gconf-cleaner yet. 

I really have no idea what I'm doing

I'm afraid to reboot because of an apparent grub-update problem.


I would appreciate some suggestion as to the direction I'm heading...

At least I would like to know that so far I'm doing things correctly.

---

### Post by red oak on 2010-06-16
OK, attempted to install gconf-cleaner

**Failed** with the following error message:


> E: linux-image-2.6.32-22-generic: subprocess installed post-installation script returned error exit status 127
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

"Dependence problem" - what does it depend on?

---

### Post by kansasnoob on 2010-06-16
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That will just give us some idea of your general setup, and also post the output of:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

And:

```
uname -a
```

---

### Post by red oak on 2010-06-16
Thank you kansasnoob

Following are the results of 3 tests as per your post: 

RESULTS.txt:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   619,193,294   619,193,232  83 Linux
/dev/sda2         619,193,295   625,137,344     5,944,050   5 Extended
/dev/sda5         619,193,358   625,137,344     5,943,987  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,137,344   625,137,282   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        55f87d8e-472a-44dc-a873-75b7983110e5   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7ef9a46b-f948-4fe2-bdce-d66a99b806b9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7263-97C0                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/7263-97C0         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
# kopt=root=UUID=55f87d8e-472a-44dc-a873-75b7983110e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=55f87d8e-472a-44dc-a873-75b7983110e5

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
uuid		55f87d8e-472a-44dc-a873-75b7983110e5
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=55f87d8e-472a-44dc-a873-75b7983110e5 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		55f87d8e-472a-44dc-a873-75b7983110e5
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=55f87d8e-472a-44dc-a873-75b7983110e5 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, memtest86+
uuid		55f87d8e-472a-44dc-a873-75b7983110e5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=55f87d8e-472a-44dc-a873-75b7983110e5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7ef9a46b-f948-4fe2-bdce-d66a99b806b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  84.6GB: boot/grub/menu.lst
  84.5GB: boot/grub/stage2
  84.6GB: boot/initrd.img-2.6.31-20-generic
  84.6GB: boot/initrd.img-2.6.32-22-generic
  84.6GB: boot/vmlinuz-2.6.31-20-generic
  84.6GB: boot/vmlinuz-2.6.32-22-generic
  84.6GB: initrd.img
  84.6GB: initrd.img.old
  84.6GB: vmlinuz
  84.6GB: vmlinuz.old

grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2 :

> grub-install (GNU GRUB 0.97)
Package: grub
State: installed
Package: grub-pc
State: not installed
Package: grub-common
State: installed
Package: os-prober
State: installed


uname -a :

> Linux red-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux


---

### Post by kansasnoob on 2010-06-16
Sorry to take so long, I got called away to gather some livestock supplies.

I'm going to look at this now and I'll let you know if I have any ideas.

---

### Post by kansasnoob on 2010-06-16
First thing, this doesn't look like a standard kernel to me:

> Linux red-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux 

Have you somehow installed a Red hat kernel?

I notice that kernel number is **2.6.31-20** but a properly updated karmic should have shown **2.6.31-[COLOR="Red"]22[/COLOR]**.

So I'd start by checking software sources and asking yourself what strange kernel you installed :confused:

---

### Post by red oak on 2010-06-16
That's very much ok **kansasnoob**, I don't expect anybody's instant attention... I appreciate the time you're taking to help... :)

Now, I have no idea where that kernel 2.6.31-20 came from.  I upgraded through the Update Manager.  Basically the system took over.

When the upgrade failed I read numerous threads and did few recommended things like:

apt-get clean
apt-get autoclean
apt-get autoremove

sudo apt-get update
sudo apt-get install -f

Could be that something got installed at that time, however ALL attempts to install, to upgrade, or to remove anything FAILED, at least that was the message I was getting.

That said, I was able to reboot the computer, which is good... but it's incredibly slow.

Is there a way to remove kernel 2.6.31-20 and replace it with the correct one?

I also noticed that it says i686.  Shouldn't that be i386?  I also have no idea where this came from:

> Linux red-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 **i686 **GNU/Linux  

Btw, red is my name, hence "red-desktop"

Thanks again for the help

---

