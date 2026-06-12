---
title: "Windows boots instead of Ubuntu after installation"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2007-04-10
Hello

I just intalled Ubuntu on my master hard drive. Windows, which was installed before, is on my other hard drive which is the slave.

The installation went fine but when I had rebooted my machine after being asked to it proceeded to load Windows as if Ubuntu hadn't been installed, it didn't even give me a choice between the two.

I'm currently running Ubuntu from the bootable CD-rom.

The master hard drive on which Ubuntu resides is partitioned as follows (according to GParted):

7.84 MB unallocated space
5.85 GB extended partition (/dev/hdg1)
--5.85 GB ntfs partition (/dev/hdg5)
67.30 GB ntfs partition (/dev/hdg2) (flags=hidden)
18.00 GB ext3 partition (/dev/hdg3) (flags=boot) <-- this is where ubuntu should be installed (2.09 GB is used on this partition so I assume it is installed)
2.00 GB swap partition (/dev/hdg4) <-- the swap partition of the installation

The slave hard drive where Windows is looks as follows in GParted:

6.46 GB ntfs partition (/dev/hdh1)
5.86 GB exntended partition (/dev/hdh2) (flags=lba)
--5.86 GB fat32 partition (/dev/hdh5) (flags=boot) <-- this is where my windows installation is
115.68 GB ntfs partiton (/dev/hdh3)
24.67 GB unallocated space

I tried removing the boot flag from my Windows partition to get it to boot into Ubuntu but now after setting the boot flag on again it won't boot into Windows so I'm forced to use the Ubuntu bootable CD-rom.

Does anyone have any ideas on how I can get my PC to give me a choice between booting Ubuntu and Windows when starting up? 

Thanks in advance.

---

### Post by bulldog on 2007-04-10
Change the master boot device in your BIOS.
You have the windows hdd as boot device I presume,make it the other one and you should see GRUB.

To boot windows from GRUB you have to make some modifications to your menu.lst.
But I tell you how it's done when you have seen the GRUB menu and you have booted ubuntu :)

---

### Post by runesvend on 2007-04-10
I've now set the Ubuntu-containing drive as the boot hard drive. Turns out I had to set it up in the configuration of my controller. The BIOS just says the boot device is ATA133RAID but I found out I had to enter the configuration of my controller and I made my secondary master hard drive my boot hard drive.

Now, where it usually says "DISK BOOT FAILURE" it says:

"GRUB Loading stage1.5."

for a couple of seconds and then reboots. If I don't touch anything it just keeps on doing this indefinitely.

Any ideas?

---

### Post by bulldog on 2007-04-10
Just to clarify,why do you use a raid controller?
You don't have any raid configuration do you?

When you installed ubuntu you have installed GRUB to the MBR of hd0 if I'm correct.
So you should boot from hd0.

Boot from the live cd and when you come to the desktop,open a terminal and type```
sudo fdisk -l
``` it's a lower case L not a one.
Copy this output to the forum.

---

### Post by runesvend on 2007-04-10
I think the raid controller is built into my mother board, my hard drives are just plugged into my motherboard and I haven't set up a raid configuration.

This is what I get from *sudo fdisk -l*:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdg: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               2         765     6136830    5  Extended
/dev/hdg2             766        9550    70565512+  17  Hidden HPFS/NTFS
/dev/hdg3   *        9551       11900    18876375   83  Linux
/dev/hdg4           11901       12161     2096482+  82  Linux swap / Solaris
/dev/hdg5               2         765     6136798+   7  HPFS/NTFS

Disk /dev/hdh: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1               1         843     6771366    7  HPFS/NTFS
/dev/hdh2             844        1608     6144862+   f  W95 Ext'd (LBA)
/dev/hdh3            1609       16709   121298782+   7  HPFS/NTFS
/dev/hdh5   *         844        1608     6144831    b  W95 FAT32

```

---

### Post by bulldog on 2007-04-10
If you boot the live cd,mount your ubuntu install
```
sudo mkdir /mnt/rescue
sudo mount /dev/hdg3 /mnt/rescue
```

If this is done,open the menu.lst```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```
and copie it to the forum.
Maybe the fstab could be useful too```
cat /mnt/rescue/etc/fstab
```
Also the output of```
cat /boot/grub/device.map
``` can be handy to see.

---

### Post by runesvend on 2007-04-11
When executing the "*gksudo gedit /mnt/rescue/boot/grub/menu.lst*" command I get this response in the terminal (not sure if it's relevant but I figured it might be):
[I]
(gedit:7143): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/I]

Here's what appears in gedit:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=0dff0ddc-1ec0-4f98-93a0-4e7888597e69 ro
# kopt_2_6=root=/dev/hdg3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdg3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdg3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdh1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


The response to "*cat /mnt/rescue/etc/fstab*":

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdg3
UUID=0dff0ddc-1ec0-4f98-93a0-4e7888597e69 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdg2
UUID=1A780D1B780CF773 /media/hdg2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdg5
UUID=A44C27514C271D94 /media/hdg5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdg4
UUID=690b41de-884e-4c38-a84b-21a63ef3ea97 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

And when executing the last command I get:

[I]ubuntu@ubuntu:~$ cat /boot/grub/device.map
cat: /boot/grub/device.map: No such file or directory[/I]

When executing this command using the path of the mounted Ubuntu install with "*cat /mnt/rescue/boot/grub/device.map*" I get:

[I](hd0)   /dev/hdg
(hd1)   /dev/hdh[/I]

in response.

I hope this helps you :).

---

### Post by bulldog on 2007-04-11
There seems nothing wrong with either the menu.lst or the fstab.
Can't see anything why it shouldn't boot.

Only thing I can sdvice is to reinstall GRUB with the live cd.
It isn't very hard to do and maybe it will solve your troubles,so try it.

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd0,2)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by runesvend on 2007-04-13
I've tried what you posted but it yields the same result, though I think I've found the problem. It's described here [http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html](http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html)

But I'm having some trouble putting this information to use, could you help me with this? I'm not sure what to do...

---

