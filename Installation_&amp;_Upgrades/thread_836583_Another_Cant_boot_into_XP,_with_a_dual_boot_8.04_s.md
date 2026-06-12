---
title: "Another Cant boot into XP, with a dual boot 8.04 setup."
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by j30a1 on 2008-06-21
Everything was working fine until I tried to remove some of the old kernels from the grub bootloader using qgrubeditor. Luckly qgrubeditor makes a backup of the old menu.lst file.  Before I figured out how to rename the old file to the current file, i tried to reinstall grub using the livecd and procedure on the standard ubuntu help.  I was able to boot back into ubuntu but I cant boot into windows xp.  When I select it on grub says "loading stage2" and then it just reloads the grub menu.  

I currently have ubuntu and xp mce installed on 1 harddrive.  I dont know how much this matters but I think it might be adding to the problem, I put xp to hibernate before I booted into ubuntu and had this problem.  This way I cant see the harddrive in ubuntu (gives the error that the system drive was in hibernation) and might make it harder to fix the xp boot problem.  

here is the output of  sudo fdisk -l
```


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       12078    96968340    7  HPFS/NTFS
/dev/sda3           12079       13968    15181425    f  W95 Ext'd (LBA)
/dev/sda4           13969       14593     5020312+  db  CP/M / CTOS / ...
/dev/sda5           13708       13968     2096451   dd  Unknown
/dev/sda6   *       12079       13632    12482442   83  Linux
/dev/sda7           13633       13707      602406   82  Linux swap / Solaris

Partition table entries are not in disk order

```

sda2 is Xp mce ,sda3 is dell backup, sda4 is embedded xp(MediaDirect)


Here is the output of this , cat /boot/grub/menu.lst


```
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
# kopt=root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b392208-6db5-4960-8255-f4b4e326dd37 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```

Here is another command,  cat /boot/grub/default
, that didnt really display anything.

```
9







#
#
#
#
#
#
#
#
#
# WARNING: If you want to edit this file directly, do not remove any line
# from this file, including this warning. Using `grub-set-default\' is
# strongly recommended.

```

If there are any ideas of how to fix this let me know.  I tried using supergrub disk but I dont really know how to use it, nor did I see anything that would help.  Thanks in advance.

---

### Post by logos34 on 2008-06-21
> **j30a1 said:**
> I dont know how much this matters but I think it might be adding to the problem, I put xp to hibernate before I booted into ubuntu and had this problem.

I agree.  Whatever you did with the kernel, it apparently didn't affect ubuntu because you can still boot it up.  What may have happened is windows got jammed up when you booted back into ubuntu: it mounted (or tried to mount) a hibernated windows partition. 

Also, I notice fdisk shows two partitions marked with a boot flag ('*')--only one should have it (windows). Remove from linux root with Gparted (right-click on sda6>'manage flags'>uncheck Boot)

> /dev/sda6   **[COLOR="Red"]*[/COLOR]**       12079       13632    12482442   83  Linux

> This way I can see the harddrive in ubuntu and might make it harder to fix the xp boot problem. 

Can you mount it and access your windows files?  If not, any error messages about  'unclean shutdown' or the like? 

> sda2 is Xp mce ,sda3 is dell backup, sda4 is embedded xp(MediaDirect)

No, I believe sda1 is Dell recovery, sda3 is the extended partition, and sda5 is the media Direct

If you have an XP install cd I would boot into the recovery console and run error checking on sda2:

**chkdsk /r**

Or see if you can enter Safe Mode in XP just before it fails and reboots.  Run chkdsk there.

---

### Post by j30a1 on 2008-06-22
Yeah i removed the boot flag from the linux root parition. 

Yeah I cant mount the windows partion, I got the error message before about how the drive was in hibernation mode or something similiar not that it was shut down improperly. 

Unfortuanately I dont have a XP cd handy,  I am still going thru SGD to see if I can fix it.

---

### Post by logos34 on 2008-06-22
> **j30a1 said:**
> I got the error message before about how the drive was in hibernation mode or something similiar not that it was shut down improperly.

oh, ok, then I guess that the 'unclean shutdown' bit only occurs when you do a hard reboot

---

### Post by meierfra. on 2008-06-22
>  i tried to reinstall grub using the livecd and procedure on the standard ubuntu help. I was able to boot back into ubuntu but I cant boot into windows xp. When I select it on grub says "loading stage2" and then it just reloads the grub menu.

I'm not sure, but this sounds like  you accidentally installed Grub to the boot sector of the  Windows partition.  So now when you try to boot windows, you get grub instead.  You can restore the boot sector via "fixboot" from the Windows CD. But you can also do  it from Ubuntu   with testdisk:


```
sudo apt-get install testdisk
sudo testdisk /dev/sda 
```

Make the following choices:

1. Screen:  Proceed  
2. Screen:  Intel
3. Screen:  Advanced
4. Screen:  Select the XP partition and  "Boot"
5. Screen:  Backup BS   (if you don't get the choice "Backup BS" it means that the boot sector and the backup are identical. In this case, you can just  quit testdisk)
After that follow the direction on the screen to write the backup  boot sector over the boot sector, and to quit testdisk.

---

### Post by j30a1 on 2008-06-26
Here is the output after i selected "backup BS"
```

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
     Partition                  Start        End    Size in sectors
 2 * HPFS - NTFS              6   0  1 12077 254 63  193936680

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

So i think I need to boot into xp to shut it down properly... 

I tried "rebuild bs" and got this:

```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
     Partition                  Start        End    Size in sectors
 2 * HPFS - NTFS              6   0  1 12077 254 63  193936680

filesystem size           193936680
sectors_per_cluster       8
mft_lcn                   806866
mftmirr_lcn               4096574
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

```

so i guess i will try to boot into xp with a xp disk once i find it.

---

### Post by j30a1 on 2008-07-22
Thanks again meiefra, using the testdisk commands work great!!

I was able to boot into this windows after this and then i just did the standard commands to reinstate grub.

```

sudo grub

find /boot/grub/stage1

returned hd0,5 for my install

then root(hd0,5)

setup (hd0,5)

quit
```

after that i got grub back!!!

---

