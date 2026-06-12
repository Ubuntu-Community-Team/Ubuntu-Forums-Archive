---
title: "Dual boot isssues"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by chubsmalone on 2006-06-22
I'm trying to dual boot dapper and Xp home on my dell laptop.  I had dapper running already, used gparted to repartition and create an NTFS partition.  I installed XP on the new partition.  I had to reinstall grub, which was fun...and now I can boot into linux, but when I try to boot into XP home, I get an error that says:

NTLDR is missing
ctrl+alt+del to restart

I know that windows has issues with being second in line, so used the map commands I've found on other posts to no avail.  I really don't know where to go from here.  My fdisk and menu.lst are posted below.

```
@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1531    12297726   83  Linux
/dev/hda2            1532        2238     5678977+   b  W95 FAT32
/dev/hda3   *        2239        3495    10096852+   7  HPFS/NTFS
/dev/hda4            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris

```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours (Default)
#color light-gray/blue black/light-gray

##Splash Image!!
splashimage (hd0,0)/boot/grub/images/schoolpisano1.xpm.gz

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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

#title		Ubuntu, kernel 2.6.12-10-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.12-10-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.12-10-386
#boot

#title		Ubuntu, kernel 2.6.12-9-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.12-9-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.12-9-386
#boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title		Microsoft Windows XP Home
map (hd0,0)  (hd0,2)
map (hd0,2)  (hd0,0)
rootnoverify	(hd0,2)
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by matko on 2006-06-23
[QUOTE=chubsmalone]I'm trying to dual boot dapper and Xp home on my dell laptop.  I had dapper running already, used gparted to repartition and create an NTFS partition.  I installed XP on the new partition.  I had to reinstall grub, which was fun...and now I can boot into linux, but when I try to boot into XP home, I get an error that says:

NTLDR is missing
ctrl+alt+del to restart

I know that windows has issues with being second in line, so used the map commands I've found on other posts to no avail.  I really don't know where to go from here.  My fdisk and menu.lst are posted below.

```
@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1531    12297726   83  Linux
/dev/hda2            1532        2238     5678977+   b  W95 FAT32
/dev/hda3   *        2239        3495    10096852+   7  HPFS/NTFS
/dev/hda4            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris

```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours (Default)
#color light-gray/blue black/light-gray

##Splash Image!!
splashimage (hd0,0)/boot/grub/images/schoolpisano1.xpm.gz

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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

#title		Ubuntu, kernel 2.6.12-10-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.12-10-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.12-10-386
#boot

#title		Ubuntu, kernel 2.6.12-9-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.12-9-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.12-9-386
#boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title		Microsoft Windows XP Home
map (hd0,0)  (hd0,2)
map (hd0,2)  (hd0,0)
rootnoverify	(hd0,2)
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST

```[/QUOTE]



lol NTLDR is important part of windows. i happent to me once so i had to reinstall it. first i would try (hd0,3)

---

### Post by chubsmalone on 2006-06-23
I tried changing it and it doesn't recognize the device.  

If I fix the MBR with a windows boot disk, I'm still in the same place because I don't want to use the windows bootloader, I'd like to use grub.  Is there any way to fix this other than repartitioning/reinstalling to put windows up front?

---

### Post by zoqaeski on 2006-06-23
Similar issue to chubsmalone, except the situation is as follows: 

New computer (Dell 5150, 1GB RAM, Pentium D 2.8 GHz, etc), freshly installed with a working Windows XP Pro system that's been plugged into Dad's server to keep the system running smoothly (as he puts it). As I had previously left space on hda to install Ubuntu, I did so using a CD burnt from the official site. All went reasonably well, although the partitioning had a few issues (it wouldn't let me use reiserfs for my home partition :confused: , but ext3 for both / and /home apparently worked fine); there were no issues booting Ubuntu either, so I finished the updates it did and then Dad suggested I boot Windows to check that installing Ubuntu didn't screw it up. Selecting the right menu in grub, this comes up:
```
Windows could not start because the following file is missing or corrupt
<Windows root>\system32\hal.dll
Please re-install a copy of the above file.
```

Now, I'm not sure what that file is supposed to do, but I'll assume that its got something to do with the bootloader. Somehow, installing Ubuntu did something to the file, although browsing to it in Nautilus reveals that it was last changed on Wed 04 Aug 2004 20:00:00 EST - well before I got this computer, or even thought about getting it.

The big question: is there a way I can resolve this dilemma without reinstalling either system?

---

### Post by roxics on 2006-07-09
I have the same problem as zoqaeski. Did you ever find a solution?

---

### Post by FrancoNero on 2006-07-09
i have a slightly related question:

if i want to use ubuntu and windows, can i use one and the same partition for swap (ubuntu) and virtual memory (windows), since both systems aren't running at the same time anyway?

---

