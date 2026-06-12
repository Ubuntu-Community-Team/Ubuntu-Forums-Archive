---
title: "Dual boot won't boot Windows on 4th/5th partition."
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by victron on 2006-08-25
Hi there everybody,

I tried in somebody else's thread to get some help for this, but it never worked out, so I'm making a new thread.

Basically I installed Ubuntu first, on the first partitition of the only drive involved in this (I have another drive but all it does is act like a "my documents" type repository).  Then I installed Windows to what I specified as the 4th partition.  Then I reinstalled Ubuntu to its original 1st partition.  Of course I had problems and stuff and tried many things during the course of all this, but that's the gist of it.

Presently, after the last fresh Ubuntu install, the only thing I have modified to GRUB is adding the following lines to my menu.lst:

```
title Windows XP.
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1
```

The reason it says hd0,4 is because Windows did a funky sort of partition stacking (please see below)... I tried with a 3 instead of 4 but it didn't work either.  The problem is I get an "error 12" when I select Windows from the GRUB menu.  

Well here's my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /music          vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb1       /storage        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Typing "sudo fdisk -l" gives me:

```
Disk /dev/hda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1305    10482381   83  Linux
/dev/hda2            1306        1371      530145   82  Linux swap / Solaris
/dev/hda3            1372        3560    17583142+   b  W95 FAT32
/dev/hda4   *        3561        4864    10474380    f  W95 Ext'd (LBA)
/dev/hda5            3561        4864    10474348+   7  HPFS/NTFS

Disk /dev/hdb: 13.6 GB, 13613064192 bytes
255 heads, 63 sectors/track, 1655 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1655    13293756    c  W95 FAT32 (LBA)

```

And lastly, this is my entire /boot/grub/menu.lst:

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

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

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title Windows XP.
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

If anybody can please tell me what is wrong and what I should do, I would greatly appreciate it.

Thank you!

---

### Post by Iarwain ben-adar on 2006-08-25
Hi,
well, assuming that your XP is the NTFS partition (/dev/hda5)
i would try to change your menu.lst to this...

```
<snip>

title Windows XP.
rootnoverify [COLOR="Red"](hd0,5)[/COLOR]
savedefault
makeactive
chainloader +1

<snip>

```

Try that, and report back :D


Iarwain

---

### Post by Eddie Hung on 2006-08-25
/dev/hda4 in your case is the "extended partition".

From what I understand, hard drives can only have 4 primary partitions. To get around this, one of the partitions can be an extended partition, in which you can create more logical partitions.

What I'm intrigued with is that Windows allows itself to be isntalled on a logical partition, and that it will boot from a logical partition too!

However, if it doesn't work, I understand that GRUB can map partitions for you too? (Run a search for more info).

Eddie

---

### Post by luvr on 2006-08-25
> **Iarwain ben-adar said:**
> ```
<snip>

title Windows XP.
rootnoverify [COLOR="Red"](hd0,5)[/COLOR]
savedefault
makeactive
chainloader +1

<snip>

```

Try that, and report back :D


Iarwain
That won't work, in my opinion--GRUB starts counting at **0,** so the fifth partition (*"hda5"*) would be partition number **4** in GRUB parlance.

To the best of my knowledge, Windows cannot boot from a *logical* partition, but requires a *primary* partition. My guess is, that it grabbed your VFAT partition, *hda3,* to boot from. If my guess is correct, then you will have to specify **(hd0,2)** for your Windows XP entry in GRUB.

---

### Post by victron on 2006-08-25
> **luvr said:**
> That won't work, in my opinion--GRUB starts counting at **0,** so the fifth partition (*"hda5"*) would be partition number **4** in GRUB parlance.

To the best of my knowledge, Windows cannot boot from a *logical* partition, but requires a *primary* partition. My guess is, that it grabbed your VFAT partition, *hda3,* to boot from. If my guess is correct, then you will have to specify **(hd0,2)** for your Windows XP entry in GRUB.

I'm typing this in Windows!

Luvr you're brilliant!!  Your comment reminded me of some annoying and useless looking system files that I deleted from my Music partition in the process of clearing out Thumbs.db and such clutter (hey, who would have thought that Windows would be stupid enough to put important system files in my MUSIC partition, which I didn't tell it to install to....I guess you can never underestimate Microsoft..).  So I went and put a few files from my trash back into my Music parition, set it to (hd0,2), and was greeted by the Windows boot loader chained after the GRUB loader.  Pretty cool.  Thank you Luvr, and here's another (I gather rather rare) example of a system that runs Windows on a non-first partition.

Thanks everybody who helped!

---

### Post by luvr on 2006-08-25
> **victron said:**
> Luvr you're brilliant!!
Well, I learned this from experience myself... Which is what made me pretty good at recognising these types of issues.

> (hey, who would have thought that Windows would be stupid enough to put important system files in my MUSIC partition, which I didn't tell it to install to....I guess you can never underestimate Microsoft..)Yeah... That's another thing I learned from experience: Pretty hard to underestimate Microsoft!

> Thank you Luvr, and here's another (I gather rather rare) example of a system that runs Windows on a non-first partition.
You're welcome! I'm doing that, too:
[LIST]
[*]My first partition is a 100-MB, ext2 **boot** partition, onto which I installed GRUB (compiled from source).
[*]My second partition is a 2-GB Linux **swap** space.
[*]My third partition is a 16-GB ***"Windows XP for Games"*** system partition, for my brother's kids. This is the system that will boot by default, and it doesn't need a password. The kids can mess it up to their heart's content, and they won't affect my main system.
[*]The remainder of the disk (some 100 GB) is assigned to the fourth partition, and currently holds my ***Main Windows XP*** system.
Once I feel sufficiently at home with Linux, I'll most likely replace this with whichever Linux distro I come to prefer--at the moment, Kubuntu looks like a serious candidate; another one is MEPIS. Or, I could still return to some more *"geeky"* distro, e.g., Slackware.
I may like to try a few other ones before making up my mind; will most likely opt for a KDE-based system in the end (even though I'm currently using GNOME-based Ubuntu).
[/LIST]
The second disk in the computer is my main Linux *"test drive,"* so to speak. :)

There's also a third disk, on which there's an additional Windows XP system, which I use for logging in to the network at the office (through VPN). I can boot this system because I use **map** commands in my GRUB configuration file, to temporarily make the system see the disk as the *first* one (since otherwise, Windows won't want to boot from it).
The remainder of the third disk is currently really just *"dump space."*

---

