---
title: "Disk Read Error Ctl-Alt-Del"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by bgoody on 2006-12-07
Hi.  Edgy works fine but on my dual boot system I am unable to boot Windows.  Gives Disk Read Errors.

Tried Super GRub Disk...same thing.
Here's the menu.lst entry

title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Output of fdisk -l:
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11897    95562621    7  HPFS/NTFS
/dev/sda2           23166       24321     9283680    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           11898       23001    89192880   83  Linux
/dev/sda4           23002       23165     1317330    5  Extended
/dev/sda5           23002       23165     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order

The Windows partition can be mounted in Edgy no problem.  Here is the Windows boot.ini:

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

Anybody have any ideas why it won't boot and what to do about it?
Thanks

---

### Post by bgoody on 2006-12-08
Somebody please?

---

### Post by bryanl on 2006-12-09
> **bgoody said:**
> Somebody please?

I am having the same problem. Made the windows recovery disks, reduced the ntfs partition, partitioned and set up the machine, installed edgy, and then find trying to boot XP gives disk read errors. 

So now I am doing a file restore recovery to the WinXP and testing those recovery disks.

This has got to be something screwed with the XP boot image. So I search and look around and experiment. If I find anything, I'll try to find this thread again to post here.

---

### Post by bgoody on 2006-12-09
That would be great if you can find a solution to this.  I'm sure it's simple.  I'm almost convinced that it isn't a Grub problem as such.

---

### Post by bryanl on 2006-12-09
The only thing I have been able to determine as a way past this is to do a power off after you resize the XP partition.

Then power up again and boot Windows.

I have had the error show up after a Windows system restore from the drive rescue partition. power down then back up and booted OK.

This is an SATA drive system ASUS mobo, phoenix bios, HP Pavilion s7620n, Intel and ATI meet Edgy.

The 3 DVD rescue disk thing takes a loooong time to restore the drive back to original for another shot. So I am leaving the 8GB restore partition in for now as it is faster.

So try a power down after resizing and see if that works. You should get the check disk as Windows comes back up.

---

