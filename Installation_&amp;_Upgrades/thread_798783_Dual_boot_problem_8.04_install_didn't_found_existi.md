---
title: "Dual boot problem: 8.04 install didn't found existing windows installation."
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by calsaverini on 2008-05-18
I'm having a problem with Hardy Heron installation. 

In the part of the installation where it's supposed to find other OS installed to add the adequate commands to Grub, it just does nothing, and I actually have a partition with windows in this hard disk. I can normally mount this partition in ubuntu and access the files.

I've tried to mannualy edit /boot/grub/menu.lst but it doesn't work.

Here is my 'fdisk -l' output:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32d3ec94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        3824    30708247+   f  W95 Ext'd (LBA)
/dev/sda3            3825        9730    47428608    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5               2        1912    15350076    7  HPFS/NTFS
/dev/sda6            1913        1974      497983+  82  Linux swap / Solaris
/dev/sda7            1975        3824    14860093+  83  Linux

```

Please note that sda5 is the partition which contains the old windows installation and sda7 is the partition with ubuntu. sda3 is just my personal files partition.

The relevant part of my menu.lst files is:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd7672d4-b381-4604-8d52-7e381b5f204d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd7672d4-b381-4604-8d52-7e381b5f204d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

[COLOR="Red"] 
#This was manually added.
title		Windows 95/98/NT/2000
rootnoverify	(hd0,4)
makeactive
chainloader	+1[/COLOR]

```

The new line appeared in the menu but when I try to boot from there, it just says:

Error 12: invalid device requested.


This is my only hard drive in this computer and I should not have to map anything, should I?
---------------------------------------------------------------------------------------------------

There are two more issues preocupating me. The first is this info in the 'fdisk -l' output:
Partition 3 does not end on cylinder boundary.

I don't know what this means, neither if it is important.

The other is the sda1 partition which I didn't created and can't mount. I don't recognize the fs type and when I try *mount /dev/sda1 /media/blabla* it asks for the filesystem type and I don't have a clue on what this *W95 Ext'd (LBA)* means.

---

### Post by meierfra. on 2008-05-18
Windows usually puts the booting information on a primary partition. So I would expect the boot files to be on sda3. Try:

title		Windows 95/98/NT/2000
rootnoverify	(hd0,2)
makeactive
chainloader	+1



(sda1 is a extended partition, it is a container for the logical partitions sda5, sda6 and sda7)

---

### Post by Pumalite on 2008-05-18
You have a Partition Table problem:
'Partition 3 does not end on cylinder boundary.'
Fix it with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by calsaverini on 2008-05-18
Partition 3 does indeed is the correct to boot, but still have problems. 

When a try to boot from this partition, I got an "bootmgr is missing" error. :(

May be this is related to the boundary issue? I installed this TestDisk thing, but it is mostly french to me. I understand very litle what this things are all about.

---

### Post by meierfra. on 2008-05-18
I don't think that your problem is caused by the boundary issue (but I'm not sure) I also don't think that testdisk can fix the boundary issue.

Did you delete any partitions when you installed Ubuntu? It might be that the booting information was on a partition you deleted.

If this is the  case  you  have to use your  WindowsCD to repair Windows.

---

### Post by calsaverini on 2008-05-18
> **meierfra. said:**
> 
Did you deleted any partitions when you installed Ubuntu? It might be that the booting information was on a partition you deleted.


Oops. Yes. When installing windows I've created three partitions and deleted one of them to create a new partition for linux. Damit.

Now I have to do those fixmbr, fixboot things and copy back the ntldr file to my windows partition. Is it right?

And install grub again... :(

---

### Post by meierfra. on 2008-05-18
I'm not sure about the exact procedure. (Never had to do it myself)

Check out this Microsoft link. It might help:

[http://support.microsoft.com/?kbid=922809&sd=RMVP]("http://support.microsoft.com/?kbid=922809&sd=RMVP")

---

### Post by Pumalite on 2008-05-18
TestDisk has a tool to fix Partition Table. Or, you can use rescueCD: 
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by meierfra. on 2008-05-18
> TestDisk has a tool to fix Partition Table.

But there is nothing wrong with the partition table. The  problems is with the partitions, not with the partition table. To fix the boundary issue one would have to resize the partitions. I don't think TestDisk can do that. 

Anyway, I don't think the boundary issue is the cause of the OP's problems.
(although I admit that I don't really know whether Window's  has problems dealing with partitions not ending on a cylindrical  boundary)

---

