---
title: "Feisty won't boot"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by girlfreddy on 2007-06-13
I just rebuilt my computer with a Gigabyte mobo, core 2 duo processor and Seagate 320 gb hard drive. Installed XP Media and partitioned the drive to fit Ubuntu and middle file system. Installed Live CD 64-bit Ubuntu and after reboot went to Ubuntu and nothing will boot from there. I get a error 17 message on everything. Now all that I've read says this is a grub problem but I haven't found anything to fix it. Can anyone help me here?

---

### Post by merlinus on 2007-06-13
Grub Error 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Perhaps

```

sudo fdisk -l

```

and

```

gksudo gedit /boot/grub/menu.lst

```

will offer some useful information.

-merlin

---

### Post by girlfreddy on 2007-06-13
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6629    53247411    7  HPFS/NTFS
/dev/sda2            6630       32125   204796620    f  W95 Ext'd (LBA)
/dev/sda3           32126       35165    24418800   83  Linux
/dev/sda4           35166       38913    30105810   82  Linux swap / Solaris
/dev/sda5            6630       32125   204796588+   b  W95 FAT32


gksudo gedit /boot/grub/menu.lst

This gave me this:

The folder contents could not be displayed. error accessing 'file:///boot/grub': File not found.

And this was on the terminal when I close the menu.lst:

Couldn't get main dbus connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by merlinus on 2007-06-13
From the last error message, it would seem that grub never got installed.

Perhaps super grub can help:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Also, what happens with this:

```

gksudo gedit /etc/fstab

```

I presume you are running these commands whilst booted into ubuntu???

-merlin

---

### Post by girlfreddy on 2007-06-13
Nope. Running them from live CD. Gotta love it!

gksudo gedit /etc/fstab gets me this:

> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda4 swap swap defaults 0 0

I'm going to look at the bigpond site now.

---

### Post by ajgreeny on 2007-06-13
Assuming you are doing the fdisk -l from the live CD, this is because there is no grub menu.lst in the live CD.  You need to mount your ubuntu partition first:-
**sudo mount /dev/sda3       /home/ -t ext3**
and then look at the menu.lst file in that partition by navigating to the /home folder in the live CD desktop.

I hope that makes sense to you and that I have got the mount command correct, but certainly sda3 is obviously your installed ubuntu partition, so I believe I've got it right.  I suspect that the menu.lst file will have a different partition noted for ubuntu and I think it is something to do with sata drive recognition in grub/ubuntu.

Good luck and let us know if it all works out and if so, exactly what you needed to do.

---

### Post by merlinus on 2007-06-13
Yeah, I kinda figured....

That's why /boot/grub/menu.lst is not coming up,  We want the one on your hard drive, as there is no such beast created whilst running from the live cd.

You will have to mount your hard drive manually.  This may help:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

The same idea will apply to mounting your hard drive as though it is an external one.

-merlin

---

### Post by merlinus on 2007-06-13
> **ajgreeny said:**
> You need to mount your ubuntu partition first:-
**sudo mount /dev/sda3       /home/ -t ext3**
and then look at the menu.lst file in that partition by navigating to the /home folder in the live CD desktop.
.

I believe you need to create the mountpoint before mounting the drive, but I may be deluded....

For example:
```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda3 /media/ubuntu

```

-merlin

---

### Post by girlfreddy on 2007-06-13
I tried just to reinstall it (after deleting the offending partitions and repartitioning) but that didn't work. Same error message when I reboot and try Ubuntu. (That's what I was doing when you guys answered me.) Now I'll go looking at what you said. And I may try and delete the middle file system and partition that through Ubuntu too. See what happens. Thanks for your help.

---

### Post by girlfreddy on 2007-06-13
> ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
mkdir: cannot create directory `/media/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda3 /media/ubuntu
mount: /dev/sda3 already mounted or /media/ubuntu busy
mount: according to mtab, /dev/sda3 is already mounted on /media/ubuntu

For menu.lst here it is:

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
# kopt=root=UUID=12152c19-05f5-40a2-b16e-f440968f1c99 ro
# kopt_2_6=root=/dev/hda1 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by merlinus on 2007-06-13
I just noticed that you re-installed, so what does

fdisk -l

look like now, before doing anything further.

-merlin

---

### Post by girlfreddy on 2007-06-13
Like dis:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6629    53247411    7  HPFS/NTFS
/dev/sda2            6630       32125   204796620    f  W95 Ext'd (LBA)
/dev/sda3           32126       35165    24418800   83  Linux
/dev/sda4           35166       38913    30105810   82  Linux swap / Solaris
/dev/sda5            6630       32125   204796588+   7  HPFS/NTFS

The last line changed because I:
1. Had only partitioned it and not formatted it when I installed XP. 
2. Thought I could format it when I installed Ubuntu.
3. That didn't work and so I thought that maybe the partitioner wouldn't recognize a partition that wasn't formatted so I just formatted it as NTFS.
4. I'm a big big noob.:p

---

### Post by merlinus on 2007-06-13
> 
itle Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1


According to this, your linux kernels live in the same partition with windows (hd0,0).  It would seem that this is impossible.

First, can you use Nautilus (file manager) to look at the contents of /boot?  You should see a bunch of files that have 2.6.20-15 as part their names.

If so, I suggest first making a backup of /boot/grub/menu.lst

```

sudo cp /boot/grub/menu.lst /boot/grub/menu_old.lst

```

Then change the root lines for the linux kernels only (NOT the one for windows) to:

root (hd0,2)

Remove the live cd, and re-boot.

-merlin

---

### Post by girlfreddy on 2007-06-14
I can look at boot/, I can type numbers into boot/, I can not save boot/. It says that it is a read-only file and I do not have privileges to copy to it (at least I think it said privileges). Anyway, I'm kind of done for the night. I'll try something else tomorrow. It might mean just redoing all of it again as it seems I've quite messed this one up. :(

---

### Post by girlfreddy on 2007-06-29
I redid my xp install on front 30 of hd (after wiping with derik's) and now would like to install feisty. But I want a file system in between the two. Should I use gparted to partition a Fat32 file system and then install Feisty on left over space?

---

