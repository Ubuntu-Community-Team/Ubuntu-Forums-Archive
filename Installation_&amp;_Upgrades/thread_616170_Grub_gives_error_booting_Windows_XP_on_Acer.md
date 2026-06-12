---
title: "Grub gives error booting Windows XP on Acer"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by scoulombe on 2007-11-17
I just installed Ubunto 7.10 on a separate partition, along side of Windows XP. It is on a single hard drive on an Acer laptop.  The 1st partition is a recovery partition. The 2nd has Windows XP installed.  Grub can boot to the recovery partition but gives errors for the Windows XP partition.  Please help.  Below is all of the information I have tried. Thank-you!

sam@laptop:/$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6ed9115

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2            1020        7826    54677227+   f  W95 Ext'd (LBA)
/dev/sda3            7827       14350    52404030   83  Linux
/dev/sda4           14351       14593     1951897+  82  Linux swap / Solaris
/dev/sda5            1020        7826    54677196    7  HPFS/NTFS

sam@laptop:/$ cat /proc/partitions
major minor  #blocks  name

   8     0  117220824 sda
   8     1    8185086 sda1
   8     2          1 sda2
   8     3   52404030 sda3
   8     4    1951897 sda4
   8     5   54677196 sda5

sam@laptop:/$ sudo vi /boot/grub/menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I TRIED CHANGING the (hd0,0) TO BE (hd0,1) AND GOT ERROR...
	Error 12: Invalid device requested

ALSO TRIED (hd0,2) ... GOT ERROR ...
	Error 13: Invalid or unsupported executable format

ALSO TRIED (hd0,3) ... GOT ERROR ...
	Error 13: Invalid or unsupported executable format

ALSO TRIED (hd0,4) ... GOT ERROR ...
	Error 12: Invalid device requested

ALSO TRIED (hd0,5) ... GOT ERROR ...
	Error 22: No such partition

---

### Post by torgrot on 2007-11-17
I don't know if that was a typo but shouldn't it be root (hd0,1)  I just looked at my menu.lst  but I don't recall ever seeing the drive referred to as hda0 just hd0

torgrot

---

### Post by scoulombe on 2007-11-17
Yes sorry that's just a typo in my post, it should read "hd0" not "hda0" in all instances.
That is only an error in my post, not related to my problem though.
The original question remains, just read "hd0" where you see "hda0"

Thanks a bunch

---

### Post by meierfra on 2007-11-18
According to your fdisk windows is sda5. (sda2 is an extended partition)
So the correct name is "(hd0,4)"  (Grub starts counting at zero, so (hd0,4) stands for the 5th partition on the 1st hard drive)

So you can try 

title Windows NT/2000/XP
root (hd0,4)
savedefault
chainloader +1


But I'm pretty sure that it will not work.  The  problem is that Windows is on a logical partition (that is inside the extended partition sda2). And it is more or less impossible to boot Windows from an logical partition, unless you also have a primary Windows partition. Did you use to have a another Windows partition?

You have two options:

1)  If you are willing to reinstall Windows: Use Gparted  to delete sda5 and sda2. Then reinstall Windows on the unallocated space.


2)  Convert the windows partition to  primary partition. I know that  this is possible in principal , but I don't know how.  Hopefully somebody reading this  thread can provide some help for that.  Or  try googling and searching the forums.

---

### Post by scoulombe on 2007-11-18
YES, I did have another Windows partition before, but it was mainly empty except for some hidden files.  So I deleted that partition to create the Linux partitions.  There is also the Recovery Partition in sda1 which boots just fine.  Could I somehow keep everything that is currently on the extended partition by overwriting the contents of sda1 to boot into Windows ?

Thanks so much !

---

