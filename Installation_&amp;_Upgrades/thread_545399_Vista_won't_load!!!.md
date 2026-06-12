---
title: "Vista won't load!!!"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by krugman on 2007-09-07
Hello,

I got a new laptop a few weeks back, and I decided to install Linux on it. After trying a few distro, I have settled on Kubuntu Fesity.
The thing is, it seems that during this process of installation, my Vista partition has been "compromised": indeed, when I start my laptop, Grub usually does not load, and I direclty boot to Kubuntu. However, when I restart the comp, Grub loads, but when I select Vista, it does not work, it keeps coming back to GRUB.
However, note that  this partition is seen under Ubuntu and is mounted.
Here is the output of a fdsik -l:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        2542    18876375    7  HPFS/NTFS
/dev/sda3            9332        9730     3191808   17  Hidden HPFS/NTFS
/dev/sda4            2543        9331    54532642+   f  W95 Ext'd (LBA)
/dev/sda5            4501        9200    37752718+   c  W95 FAT32 (LBA)
/dev/sda6            9201        9331     1052226   82  Linux swap / Solaris
/dev/sda7            2543        4500    15727572   83  Linux

Partition table entries are not in disk order

```

and my etc/fstab:


```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=895b7660-4f88-4845-a363-f86c0c23169d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=AC8CC4088CC3CAD2 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=88D6C94CD6C93B68 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=1A18CFA418CF7D6F /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=46CE-A9AA  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=af3b22ca-e7a3-46e9-a7aa-e822ae4a100e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I have already had a few problems with GRUB, but never one like this one. I know this is a very sensitive issue, and I don't want to lose some date. Well, I have got everything saved, but I would prefer not to have to reinstall both Vista and kubuntu.
What are my options? I guess I can either: (i) try to reinstall vista in the first partition; (ii) repair GRUB with Ubuntu.
Can I do something else? What is the best option?

Thanks for any help.

EDIT: sda2 is my vista partition; sda1 is a hidden recovery partition

---

### Post by Pumalite on 2007-09-07
Post:
cat /boot/grub/menu.lst

---

### Post by merlinus on 2007-09-07
What I find interesting is that the partition numbers are not in the order in which they are on the hdd.

I recall another instance of this recently, which led to a complete dban and starting over.

-merlin

---

### Post by Pumalite on 2007-09-07
I had a similar feeling, but wanted to see the menu.lst first.

---

### Post by krugman on 2007-09-07
Thanks guys! here is my menu.lst:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=895b7660-4f88-4845-a363-f86c0c23169d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=895b7660-4f88-4845-a363-f86c0c23169d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=895b7660-4f88-4845-a363-f86c0c23169d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=895b7660-4f88-4845-a363-f86c0c23169d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

##title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
##root		(hd0,6)
##kernel		/boot/vmlinuz-2.6.20-15-generic ##root=UUID=895b7660-4f88-4845-a363-f86c0c23169d ro single
##initrd		/boot/initrd.img-2.6.20-15-generic

##title		Ubuntu, memtest86+
##root		(hd0,6)
##kernel		/boot/memtest86+.bin
##quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
rootnoverify		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


```

---

### Post by Pumalite on 2007-09-07
Backup and edit your menu.lst, and remove the last entry for Vista in sda3. Save, exit reboot and let's see.

---

### Post by krugman on 2007-09-08
Well, I tried that, but nothing changed!
I guess I will have to try to reinstall Vista, but it is sooo slow...
Moreover, I am not sure it will actually solve the problem...

---

### Post by Pumalite on 2007-09-08
My suspicion is that this is the problem: /dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.

Check the hard drive well and make your partitions carefully.

---

### Post by krugman on 2007-09-08
Hello,

what do you mean by "check your hard drive...and make your partitions carefully".
Because sda1 and sda3 are both pre-installed partitions on my laptop, and I didn't do anything with them.

Do you think I have to reinstall everything?

---

### Post by Pumalite on 2007-09-08
That's exactly the problem. You are trying to install where Microsoft doesn't want you to install anything. They usually leave the drives littered with these 'rescue partitions' when they should give you a disc. We've had cases here where they had to DBaned the drives first.

---

### Post by krugman on 2007-09-08
Yes, this is indeed a problem.
However, I must say that at first, I was able to boot into Vista. Thus,  it used to work.

---

### Post by merlinus on 2007-09-08
Use supergrub to try to boot vista.

d/l here:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

More info, if needed, here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by krugman on 2007-09-08
Ok, I have read the tutorial for Super Grub, but it seems it can only allow me to boot to Vista once, but not to repair it right?
Well, anyhow, I will try it tomorow.

---

### Post by merlinus on 2007-09-08
No, there is an option to restore the bootloader to your windows partition.

-merlin

---

### Post by krugman on 2007-09-11
Ok, so I have experimented with Super Grub, but Vista still won't load!
The thing is, I haven't found which option to use to restore the bootloader. I have found one to restore windows bootloader, but I don't think it is this one.
I don't want to make a mistake and render my ubuntu partition unbootable:(

---

### Post by merlinus on 2007-09-11
At this point, if you still want vista, it seems that restoring its bootloader to the mbr is the only way forward.  You can use your vista cd (dvd) for this.

Boot into recovery console (or something like that), and look for an option like fixboot or fixmbr.

Once vista is bootable, you should be able to reinstall grub in order to get a menu to choose between the two.

---

### Post by krugman on 2007-09-11
well, I am not sure I need Vista anymore.
I have installed Virtualbox, and I guess this is sufficient for my needs.

I have to solve a few problems first, but it will be fine I think.

---

### Post by merlinus on 2007-09-11
Good luck!  And let us know how it goes....

---

### Post by krugman on 2007-09-14
Just one last quick question: since my Vista partition won't load, I was considering removing it with qparted and replacing it with a ext3 partition since I need more room.

Would it be a problem? Is there a risk that I ruin my GRUB?

---

### Post by splintercellguy on 2007-09-14
Most likely not, the MBR boot code won't be altered.

---

