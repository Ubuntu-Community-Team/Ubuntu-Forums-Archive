---
title: "Confused by GRUB"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by ranger0293 on 2007-03-30
I apologize if the following seems confusing, but in reality it is confusing and I need some people with brains bigger than mine to figure it out.

I have a system with Windows Vista currently installed on it.  This system has 4 SATA hard drives as follows:
SATA1 - 80GB drive with Vista on it
SATA2 - 300GB drive for media
SATA3 - 200GB drive for media
SATA4 - 120GB drive for Linux

I installed Vista first, and everything is working fine.  I then installed Ubuntu.  Oddly enough, when it presented me a list of my disks, they were in a different order, as seen below:
SATA2 - 300GB - /dev/sda
SATA4 - 120GB - /dev/sdb
SATA1 - 80GB - /dev/sdc (Vista installed here)
SATA3 - 200GB - /dev/sdd

So I installed to /dev/sdb, and installation went okay, except for GRUB, which was installed to the default hd0.  When I reboot, the Vista bootloader started up and took me straight to Vista.

Does anyone have any instructions on to how to get GRUB to be my bootloader?  I don't mind reinstalling Linux and giving it a different hd if that's necessary.  I don't quite understand the GRUB commands, but I'm comfortable doing it and following instructions.

---

### Post by temis01 on 2007-03-30
If you installed grub on /dev/sdb you have to boot from this HD to be able to boot into ubuntu
so in bios just select the HD corresponding to /dev/sdb or press the relevant key to choose hd to boot during bios post (recent mobo)
If you want to boot into vista grub must have created a line for this in the grub menu.

> **ranger0293 said:**
> I apologize if the following seems confusing, but in reality it is confusing and I need some people with brains bigger than mine to figure it out.

I have a system with Windows Vista currently installed on it.  This system has 4 SATA hard drives as follows:
SATA1 - 80GB drive with Vista on it
SATA2 - 300GB drive for media
SATA3 - 200GB drive for media
SATA4 - 120GB drive for Linux

I installed Vista first, and everything is working fine.  I then installed Ubuntu.  Oddly enough, when it presented me a list of my disks, they were in a different order, as seen below:
SATA2 - 300GB - /dev/sda
SATA4 - 120GB - /dev/sdb
SATA1 - 80GB - /dev/sdc (Vista installed here)
SATA3 - 200GB - /dev/sdd

So I installed to /dev/sdb, and installation went okay, except for GRUB, which was installed to the default hd0.  When I reboot, the Vista bootloader started up and took me straight to Vista.

Does anyone have any instructions on to how to get GRUB to be my bootloader?  I don't mind reinstalling Linux and giving it a different hd if that's necessary.  I don't quite understand the GRUB commands, but I'm comfortable doing it and following instructions.

---

### Post by Scunizi on 2007-03-30
Welcome to the wonderful wacky world of GRUB.  At least to nOOb's like me.  I'm not sure which version of Ubuntu you're using but I'm on Dapper.  With Dapper, it got confused with a mix of 2 SATA drives and one IDE and on install it managed to put GRUB on the wrong drive.  I suspect that's the malady you're suffering.  

It took a couple of readings to figure out how grub labels my drives verses how the system identifies them.  The resource I used to fix my grub is located here... [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm).  One of the things I cought when re-reading it was to install grub on the Windows drive as well as the Linux drive.  The reason being, it you have a problem with one or the other you can change the default boot drive in the bios and get right back up and running.  Happy Ubuntu-ing!:)

---

### Post by ranger0293 on 2007-03-30
> **temis01 said:**
> If you installed grub on /dev/sdb you have to boot from this HD to be able to boot into ubuntu
so in bios just select the HD corresponding to /dev/sdb or press the relevant key to choose hd to boot during bios post (recent mobo)
If you want to boot into vista grub must have created a line for this in the grub menu.
I told my BIOS to boot from that disk, and GRUB started up okay.  I had the various ubuntu options, as well as a Vista/Longhorn option.

When I selected the ubuntu option, I got the following:
Error 17: Cannot mount selected partition.

When I selected the Vista option, I got:
NTLDR Not Found

Any ideas?

---

### Post by confused57 on 2007-03-31
> **ranger0293 said:**
> I told my BIOS to boot from that disk, and GRUB started up okay.  I had the various ubuntu options, as well as a Vista/Longhorn option.

When I selected the ubuntu option, I got the following:
Error 17: Cannot mount selected partition.

When I selected the Vista option, I got:
NTLDR Not Found

Any ideas?

You might want to boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list
and finally
```
cat /boot/grub/device.map
```

I believe you just need to add a Window's entry to boot Vista similar to the one in this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Sorry, just re-read your last reply, you can't boot Ubuntu yet...for now, boot up the live cd and post the output of "sudo fdisk -l"...that should get us started for finding a solution.

Added:  Here's something you can try first to boot into Ubuntu, at the grub menu, highlight your Ubuntu entry, press "e", then change root to (hd0,x), then press "b" to boot...x means to leave this entry as it is.   This change is temporary, but can be made permanent if it works.

---

### Post by al7kz on 2007-04-01
deleted

---

### Post by ranger0293 on 2007-04-01
Forgive me for taking so long to reply.

I booted up GRUB and did the 'e' trick to change the root to (hd0,0).  This worked fine (I'm booted up in linux right now).  So, now all I really need is to get that change to be permanent, and to get my Vista option fixed.  

Here's my fdisk -l
```
root@desktop:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      620178   312569680+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14216   114189988+  83  Linux
/dev/sdb2           14217       14593     3028252+   5  Extended
/dev/sdb5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       24321   195358401    7  HPFS/NTFS
root@desktop:~# 
```

And here's the applicable parts of my menu.lst (I removed the extraneous menu options like recovery and memtest)
```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

Seems like maybe I want to change that root line to hd(0,0)?  Not really sure how to touch my Vista one, however.

Just a reminder, but the NTLDR is loaded on /dev/sdc (hd2).

---

### Post by confused57 on 2007-04-01
To make the grub changes permanent, boot into Ubuntu, open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
copy & paste each line one at a time, press enter after each line

change your root in the kernel lines to (hd0,0)

also, you need to change this line:
```
# groot=(hd1,0)
```
to
```
# groot=(hd0,0)
```
quit & save changes

you'll still need to post the output of:
```
cat /boot/grub/device.map
```

---

