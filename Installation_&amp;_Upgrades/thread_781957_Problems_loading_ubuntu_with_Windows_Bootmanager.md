---
title: "Problems loading ubuntu with Windows Bootmanager"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by billis on 2008-05-04
Hell,

I want to use the Windows Vista Bootmanager for booting Vista and Ubuntu. I've installed Ubuntu on a second hard drive and selected to install its bootloader (grub) on the Ubuntu partition, so it won't overwrite my MBR.

I booted then with the LiveCD and extracted the Bootloader from the ubuntu partition with ```
dd if=/dev/sdb1 of=[USB-STICK]/linux.mbr bs=512 count=1
```
Then I rebooted into Windows Vista and made an entry in the Bootmanager for my Ubuntu installation.

All seemed to worked fine, but when I select "Ubunut" to boot, there comes only a black text screen with the message "GRUB" and nothing happens.

Anyone knows what I did wrong or what I've to do?

My system configuration:

dev/sda -> Windows hard disk with several partitions
/dev/sdb -> Hard disk, I've installed ubunutu on, with following partitions:
/dev/sdb1 -> root
/dev/sdb2 -> /home
/dev/sdb3 -> swap
/dev/sdb4 -> ntfs (used with Windows)

I would be grateful for your help!

Greets,
bill

---

### Post by billis on 2008-05-05
No one? :(

---

### Post by billis on 2008-05-11
Still having this problem :-(

---

### Post by meierfra. on 2008-05-11
Your approach does not work since ubuntu is on /dev/sdb but you are booting from /dev/sda. To fix the problem you need to temporarily install grub to a partition on /dev/sda. See

[http://ubuntuforums.org/showpost.php?p=4004058&postcount=25]("http://ubuntuforums.org/showpost.php?p=4004058&postcount=25")

for detailed instruction.

But in the line

```
sudo mount -t ntfs /dev/sda2 /windows 
```

you need to replace "/dev/sda2" by the actual location of your windows partition. (Or you can use your USB stick for this step)

Also you can use "linux.mbr" in place of "ubuntu.dos". Then you won't have to edit "boot.ini" again.

---

### Post by billis on 2008-05-11
Thank your for your support!

I followed the instructions explained in the link you gave me, but 	unfortunately I get exactly the same behaviour. When I select ubuntu, I get a text screen with the message "GRUB" on the top left.

What I did:
I booted with the Live CD. Then, first I backuped my MBR of sda and my Partition Boot Record of sda1.
Then I installed grub ( root(hd1,0); setup (hd0,0) ).
After that, I copied the Partition Boot Record of sda1 to a file on a usb stick (LINUX.MBR) and wrote the MBR and PBR of sda/sda1 back.

Any other ideas?

---

### Post by meierfra. on 2008-05-11
Lets just see whether you can boot into Ubuntu via  Grub:

Try these:


1)
     sudo grub 
     root (hd1,0)
    setup (hd1)

and reboot from your second hard drive

or 

2) 

   sudo grub 
   root (hd1,0)
   setup (hd0)

and reboot from your first hard drive.  

This overwrites your MBR  but since you already backuped your MBR you will be able to restore it  if needed.

If none of this works  post  your menu.lst (let me know if you need help with that) and the output of

sudo fdisk -l

(l is a lowercase L)

---

### Post by billis on 2008-05-12
Ok, I got my Ubuntu booting with installing grub in the MBR of sdb.

I booted with selecting my second hard drive via the boot menu of my motherboard. It's sort of weird that I had to change the root (hd1,0) to root (hd0,0) in the grub menu to boot. Maybe my motherboard sets the booting-hd to device 0 ???

Anyway, I copied the MBR of sdb again in a file and used it for booting with the Vista Bootmanager. Again the same, nothing happens. My conclusion is that maybe the Vista Bootmanager has a problem booting other hard drives?

Here are my setting files for grub you wanted:

device.map
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

fdisk -l
```
Platte /dev/sda: 750.1 GByte, 750156374016 Byte
255 Köpfe, 63 Sektoren/Spuren, 91201 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xa1d4a08b

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6375       30695   195352576    7  HPFS/NTFS
/dev/sda3           30695       48935   146513920    7  HPFS/NTFS
/dev/sda4           48935       91202   339505152    f  W95 Erw. (LBA)
/dev/sda5           48935       73256   195352576    7  HPFS/NTFS
/dev/sda6           73256       85416    97676288    7  HPFS/NTFS
/dev/sda7           85416       91202    46473216    7  HPFS/NTFS

Platte /dev/sdb: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x898daf85

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1        2739    22000986   83  Linux
/dev/sdb2            2740        3361     4996215   83  Linux
/dev/sdb3            3362        3610     2000092+  82  Linux Swap / Solaris
/dev/sdb4            3611       30402   215199744    f  W95 Erw. (LBA)
/dev/sdb5            3611        4133     4199424    7  HPFS/NTFS
/dev/sdb6            4134       25020   167772160    7  HPFS/NTFS
/dev/sdb7           25020       30402    43225088    7  HPFS/NTFS

Platte /dev/sdc: 120.0 GByte, 120034123776 Byte
255 Köpfe, 63 Sektoren/Spuren, 14593 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x87d93992

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1               1       14594   117218304    7  HPFS/NTFS

Platte /dev/sdd: 64 MByte, 64487424 Byte
255 Köpfe, 63 Sektoren/Spuren, 7 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x000ef3b2

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdd1   *           1           8       62944+   e  W95 FAT16 (LBA)
Partition 1 hat unterschiedliche phys./log. Enden:
     phys=(6, 254, 63) logisch=(7, 214, 15)

```

menu.lst
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=486a19e8-654d-4574-a2c6-33e3a1b40fa9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=486a19e8-654d-4574-a2c6-33e3a1b40fa9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1
```

---

### Post by meierfra. on 2008-05-12
>  It's sort of weird that I had to change the root (hd1,0) to root (hd0,0) in the grub menu to boot.
During booting grub always sees the drive you are booting from as (hd0).


But I do not understand why my method did not work. Could be Vista's fault. I only tried it with XP.

Anyway you could just set your bios to boot from your second hard drive and all your problems are solved (the mbr in your first hard drive is still intact and you can boot into windows and ubuntu)

As you already realized  you need to edit your menu.lst:

Change all "root (hd1,0)" to "root (hd0,0)"  
Change "#groot (hd1,0)" to "#groot (hd0,0)" (otherwise you run into trouble after the next kernel update)

Change

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

to 

title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
chainloader	+1


( if Vista does not boot from the grub menu, add

map (hd0) (hd1)
map (hd1) (hd0)

but I believe Vista does not need the map statements, only XP does.)

---

### Post by meierfra. on 2008-05-12
You can also try [URL="http://neosmart.net/dl.php?id=1"]
EasyBCD[/URL]

EasyBCD is a really nice boot loader for Vista.

---

### Post by billis on 2008-05-12
EasyBCD did it!!

I've installed it and created a menu entry with the option, that Grub isn't on the MBR and it made a bootrecord file for the new entry. It seems that it has it's own bootmanager called "NeoGrub" that calls finally my Grub. Anyway, it works :-)

What I'm suprised at, now I have to tell Grub ```
root (hd2,0)
``` to boot :confused:

Thank very much you again for your support!!

Greets,
bill

---

### Post by meierfra. on 2008-05-12
> root (hd2,0)

Do you have three hard drives?  Maybe that's  why the earlier attempts failed. 


> 
Thank very much you again for your support!!

Gern geschehen.

---

### Post by billis on 2008-05-12
> **meierfra. said:**
> Do you have three hard drives?  Maybe that's  why the earlier attempts failed.
Yes, I have three harddrives, the third one is sdc (who wonders :-D) and it's not marked as active. So I can't figure out why this should be the problem for the first attemps.

The sdc drive is also listed in the fdisk output, if you want to look closer.

> **meierfra. said:**
> Gern geschehen.
Hey, you speak german :-) You ARE german?? :-D

---

### Post by meierfra. on 2008-05-12
> The sdc drive is also listed in the fdisk output,

Oops, I missed that.

> and it's not marked as active.

Grub does not care whether a drive is active or not.
And the real problem is that the grub in the terminal sometimes numbers the   hard drives different than the grub at boot up. (Because the grub in the terminal has no knowledge about the boot order)

So this what happened: "root (hd1,0), setup (hd0,0)" told grub to look for "menu.lst" on (hd1,0)" But during boot-up, grubs thinks "(hd1,0)"  is  your third hard drive and cannot find "menu.lst"


This  problem could be fixed by either changing the boot order in the bios, or  by editing the device map and run "grub  --device-map=device.map"

But thanks to Easy BCD you don't have to worry about that.


> You ARE german?? 

Yes, but live in Michigan, USA.

---

### Post by billis on 2008-05-12
Ok, thanks for the explanation!
Long live EasyBCD ;-)

> Yes, but live in Michigan, USA.
Well, I'm not, but I live in Stuttgart, Germany :-D

Wie klein doch die Welt ist :-)

---

