---
title: "[SOLVED] GRUB Woes"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by blueorder on 2007-07-04
Sorry for the double post (posted on Absolute Beginners forum) but I think this is the correct location for this. Mods, please delete post from Absolute Beginners forum. Thx.

----------------------------------------------------------

I use Windows XP and wanted to dual boot XP and Ubuntu.

I have a 75GB primary SATA drive that ubuntu install sees as **hde** and an IDE 120GB data drive that ubuntu install sees as hda.

I resized the drive XP is on (hde) and created the following partitions:

mount Windows partition as /windows (hde1)

swap --> 3GB
/ --> 20GB
/home --> 27GB

After install, I rebooted and it went straight into Windows XP without showing GRUB on POST.

I reinstalled, and clicked on advanced on the review screen and saw that the drive to install GRUB was designated as **(hd0)** which I figured is my data drive as it is seen as hda. I switched (hd0) to **(hd1)** and after install/reboot, GRUB popped up on POST but after selecting Ubuntu and error appears saying something to the effect of "cannot find partition" and if I ESC back to menu and select Windows XP it shows an error saying that it cannot find NTLDR.

Any suggestions?

TIA

---

### Post by logos34 on 2007-07-04
When you get to the grub menu screen, highlight ubuntu kernel and hit 'e' to edit.  I think the root line will read '**root (hd1,2)**',  Change to **(hd[COLOR="Red"]0[/COLOR],2)**.  Make sure to hit 'enter' after the edit. Then if that allows you to boot linux go into /boot/grub/menu.lst and change the entries accordingly for ubuntu kernels and windows, which should be **(hd[COLOR="Red"]0[/COLOR],0)**

/boot/grub/device.map should read:

(hd0) /dev/hde
(hd1) /dev/hda

Why is linux seeing your sata as 'hde' (and not 'sde')?  Which ubuntu release are you suing?  If feisty, I would also expect it to see both drives as 'sd?' (uses scsi device ID subsystem)

---

### Post by logos34 on 2007-07-04
i'm just guessing these are all primary partitions (in the order you listed them).  

you might want to post the output from

**sudo fdisk -l**

---

### Post by blueorder on 2007-07-04
I had recovered my system drive from ghost image but I'm in the LiveCD again ready to reinstall.

Here's the output from fdisk -l:

```
Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        3825    30724281    7  HPFS/NTFS
/dev/hde2            3826        4217     3148740   82  Linux swap / Solaris
/dev/hde3            4218        6827    20964825   83  Linux
/dev/hde4            6828        9729    23310315    5  Extended
/dev/hde5            6828        9729    23310283+  83  Linux

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14593   117218241    7  HPFS/NTFS

```

Oh, and by the way, it is Feisty that I'm trying to install.

EDIT: I added all the partitions with GParted.

---

### Post by blueorder on 2007-07-04
I attached a screen of the partitions during install.

---

### Post by blueorder on 2007-07-05
Got it to boot by changing the line in menu.lst from (hd1,1) to (hd0,1). After booting I changed all the entries in menu.lst.

One question, there was a kernel upgrade to download and all the settings in menu.lst reverted to (hd1,1). Am I going to have to change these every time there is a kernel update?

Here's my menu.lst for reference:

```

default		0

timeout		10

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e36bba0-9adb-437c-91d7-064ca782e070 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e36bba0-9adb-437c-91d7-064ca782e070 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2e36bba0-9adb-437c-91d7-064ca782e070 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2e36bba0-9adb-437c-91d7-064ca782e070 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I took out most of the commented stuff to save space.

Thanks,

---

### Post by logos34 on 2007-07-05
> Got it to boot by changing the line in menu.lst from (hd1,1) to (hd0,1).

You mean (hd1,2) to (hd0,2).  Because that's what the menu.lst shows.  (Otherwise you'd be booting to hde2, thus becoming the first in history to boot a swap partition!)

> title		Ubuntu, kernel 2.6.20-16-generic
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e36bba0-9adb-437c-91d7-064ca782e070 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

That's what I thought you needed.  
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        3825    30724281    7  HPFS/NTFS
/dev/hde2            3826        4217     3148740   82  Linux swap / Solaris
/dev/hde3            4218        6827    20964825   83  Linux
[B]/dev/hde4            6828        9729    23310315    5  Extended
/dev/hde5            6828        9729    23310283+  83  Linux[/B]

Ok, so you have an extended partition containing swap.
> 

 One question, there was a kernel upgrade to download and all the settings in menu.lst reverted to (hd1,1). Am I going to have to change these every time there is a kernel update?

Did you change the 'groot' line to match the kernels?

> ## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,2)**

---

