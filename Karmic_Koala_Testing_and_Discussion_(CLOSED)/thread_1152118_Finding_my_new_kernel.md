---
title: "Finding my new kernel"
date: 2009-05-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by davideotape on 2009-05-07
After installing the new kernel today (2.6.30), my grub says it can't find the file, although booting off the old jaunty kernel still works. This is my menu.lst:
```

default		6

timeout		4

title		Ubuntu karmic (development branch), kernel 2.6.30-2-generic
uuid		36d818c5-b05d-48cb-a2a5-ed843c67bfc4
kernel		/boot/vmlinuz-2.6.30-2-generic root=UUID=36d818c5-b05d-48cb-a2a5-ed843c67bfc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.30-2-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.30-2-generic (recovery mode)
uuid		36d818c5-b05d-48cb-a2a5-ed843c67bfc4
kernel		/boot/vmlinuz-2.6.30-2-generic root=UUID=36d818c5-b05d-48cb-a2a5-ed843c67bfc4 ro  single
initrd		/boot/initrd.img-2.6.30-2-generic

title		Ubuntu karmic (development branch), kernel 2.6.28-11-generic
uuid		36d818c5-b05d-48cb-a2a5-ed843c67bfc4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=36d818c5-b05d-48cb-a2a5-ed843c67bfc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		36d818c5-b05d-48cb-a2a5-ed843c67bfc4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=36d818c5-b05d-48cb-a2a5-ed843c67bfc4 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		36d818c5-b05d-48cb-a2a5-ed843c67bfc4
kernel		/boot/memtest86+.bin
quiet


title		Other operating systems:
root



title		Windows Vista
rootnoverify	(hd0,0)
savedefault
chainloader	+1


title		Windows Vista Recovery
rootnoverify	(hd0,1)
savedefault
chainloader	+1


title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2d6eba4a-670f-447e-a46e-1428027e6e5a ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2d6eba4a-670f-447e-a46e-1428027e6e5a ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot

title		Ubuntu 9.04, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

``` (with comments removed)

This is on /dev/sdb1, and my karmic install is on /dev/sdd5 (my external hard drive)

Anyone know what I've done wrong?

All help appreciated :D

David

---

### Post by Reiger on 2009-05-08
Me thinks that your Karmic kernel entries point to a (non-existing location) on your sdb**1**. Which is to say, you may want to edit a line to read something akin to:
```

root (hd3,5) # this is in Grub-hdd-speak: fourth hd (first is hd0), partition #5 (2nd or 3rd logical partition)

```
Which AFAIK maps to /dev/sdd5 in Linux-hdd-speak. Be sure to check double check this, though: plenty of resources on the net and better safe than sorry here. ;)

---

### Post by davideotape on 2009-05-08
Thanks for the help Reiger. After a bit of trial and error (and forgetting you can edit directly from grub:roll:), I put in (hd2,4) and got the error message 13 (probably same as this post: [http://ubuntuforums.org/forumdisplay.php?f=359]("http://ubuntuforums.org/forumdisplay.php?f=359"))

What I don't understand is why I don't need the hd bit for the 2.6.28 kernel.

---

### Post by Reiger on 2009-05-08
Well usually grub will find your stuff by UUID: I was merely speculating that the reason why this failed for your external HDD was that Grub doesn't recognise/know from its UUID it should look at /dev/sdd5 instead. The "root (hdx,y)" format is actually a mechanism for Grub to launch arbitrary OS'es which cannot be launched using a UUID (like Windows).

Something that may be a good idea, is to install Grub to the MBR of your external HDD and simply change the preference order in your BIOS to try and boot from USB/removable-device first, and from internal HDD's next.

---

### Post by davideotape on 2009-05-08
Yes, that would be a good idea. I have had problems booting to the same partition that grub is on before though.

```
[B]david@ExternalHarddrive:~$ sudo fdisk -lu
[sudo] password for david: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   477757034   238878486    7  HPFS/NTFS
/dev/sda2       477757035   488097130     5170048    7  HPFS/NTFS
/dev/sda3       488097792   488394743      148476    7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b96ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    38122244    19061091   83  Linux
/dev/sdb2        38122245    39873329      875542+   5  Extended
/dev/sdb5        38122308    39873329      875511   82  Linux swap / Solaris

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x409df437

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63    15631244     7815591   83  Linux
/dev/sdd2        15631245   488392064   236380410    5  Extended
/dev/sdd5        15631308   476471834   230420263+  83  Linux
/dev/sdd6       476471898   488392064     5960083+  82  Linux swap / Solaris
david@ExternalHarddrive:~$ 
[/B]
```

My grub is on sda, with windows on sda1 and windows recovery partition on sda2. sdb is my origional install, and this is where menu.lst is located. sdd is my external hard drive, with sdd1 being my bootable livecd which I installed onto my external drive from. sdd5 is my main installation, that I'm using with karmic, and sdd6 is the swap it uses.

I think it's fair to say I'm not running a straightforward machine :P

---

