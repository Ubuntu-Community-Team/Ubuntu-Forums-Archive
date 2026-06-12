---
title: "GRUB problem - error 22!"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by FarmerJo on 2007-09-24
Hi,

I have recently installed ubuntu 7.04 on my desktop PC olong with windows xp and find that at startup GRUB reports an error 22. I am able to rewrite the MBR using the windows xp CD this this, of course, all deletes GRUB andtherefore I cannot start ubuntu.

It would appear that for some reason GRUB has not been configured correctly. What I would like to do is to manually edit the GRUB configuration files on the PC but cannot since it won't boot.

Where are the configuration files stored and what are the filenames? Can these be accessed and edited by using the ubuntu CD? My PC has two hard drives in it and ubuntu has been installed on the second drive (hdb) using the usual two partitions (I think these are hdb2 and hdb5 but not sure).

Any help would be appreciated.

Regards FarmerJo

---

### Post by malfist on 2007-09-24
Make sure it's installing on that other hard drive. When I've seen error 22 is when someone installs ubuntu on an external device or a pen drive by accedent and GRUB can't find it.

---

### Post by meindian523 on 2007-09-24
> **FarmerJo said:**
> Hi,

I have recently installed ubuntu 7.04 on my desktop PC olong with windows xp and find that at startup GRUB reports an error 22. I am able to rewrite the MBR using the windows xp CD this this, of course, all deletes GRUB andtherefore I cannot start ubuntu.

It would appear that for some reason GRUB has not been configured correctly. What I would like to do is to manually edit the GRUB configuration files on the PC but cannot since it won't boot.

Where are the configuration files stored and what are the filenames?

The main configuration file associated with Grub is /boot/grub/menu.lst.

> **FarmerJo said:**
>  Can these be accessed and edited by using the ubuntu CD?
Yep it can be done by mounting your root partition(mount point "/") 

> **FarmerJo said:**
> My PC has two hard drives in it and ubuntu has been installed on the second drive (hdb) using the usual two partitions (I think these are hdb2 and hdb5 but not sure).
That's not a problem....do a ```
 sudo fdisk -l
``` in terminal in Ubuntu Live CD.....you will be given complete details of all partitions including partition name,filesystems,size,start sector and end sector...........

> **FarmerJo said:**
> Any help would be appreciated.

Now appreciate......;) :-P

---

### Post by FunkyJack on 2007-09-24
And check that you WinXP isn't installed on extended logical partition.
Yesterday i had to reinstall win 2 times because stupid win can't boot from extended partition. ](*,)

---

### Post by FarmerJo on 2007-09-24
Hi,

I have used the installation CD in an attempt to see where GRUB is going wrong at boot up. The menu.lst file contents are as follows. Please excuse the length of text here.

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
# kopt=root=UUID=05133831-c6d5-469c-b351-e695cea8af5a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=05133831-c6d5-469c-b351-e695cea8af5a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=05133831-c6d5-469c-b351-e695cea8af5a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

----------------------------------------------------------------------------------------------------------
Also I ran a terminal with the command sudo fdisk -l and got the following partition information.

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        7297    43255012+   7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5608    45046228+   7  HPFS/NTFS
/dev/hdb2   *        5609        7220    12948390   83  Linux
/dev/hdb3            7221        7297      618502+   5  Extended
/dev/hdb5            7221        7297      618471   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
----------------------------------------------------------------------------------------------------------

Can anyone tell me if there is a glaring problem with the way that GRUB has been configured given my hard-drive and partition configuration?

Regards FarmerJo

---

### Post by Pumalite on 2007-09-24
I reviewed it, I thought I had seen something, but not; on 2nd view it seems OK.
You could try re-installing Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by FarmerJo on 2007-09-24
Thanks for time. It is appreciated.
FarmerJo

---

### Post by Pumalite on 2007-09-24
You are welcome. I wish you good luck with the re-install if you decide to do it.

---

### Post by FarmerJo on 2007-09-25
After thinking about it overnight I did this.

Disconnected the second hard-drive (where ubuntu was being installed on initially) and re-installed again. This time the installation was to the first hard-drive along with windows xp.

Now I am able to dual boot the PC as needed. I am still none the wiser why GRUB did not work correctly when ubuntu was installed on the other drive.

Are there any known issues with GRUB?

Regards
FarmerJo

---

### Post by Pumalite on 2007-09-25
Mapping might have helped with that prior condition.

---

### Post by meindian523 on 2007-09-25
> **Pumalite said:**
> Mapping might have helped with that prior condition.

What mapping btw??

---

### Post by FarmerJo on 2007-09-25
Dare I ask what mapping is?

---

### Post by Pumalite on 2007-09-25
Telling Grub that there are two drives, and where they are.

---

### Post by meindian523 on 2007-09-27
> **Pumalite said:**
> Telling Grub that there are two drives, and where they are.

and how do we do that....I guess the root (hd1,Y) part in the menu.lst is enouf to tell Grub that there are two HDDs,correct?since hd0 is obviously the first HDD.....:)

---

