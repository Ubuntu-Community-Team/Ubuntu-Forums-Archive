---
title: "Dual Boot Issue"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by bradhawk08 on 2008-01-22
Here's what I want to do:

I have linux installed on my laptop, and i have an external hard drive that has XP installed on it.  I want to set up the grub that is installed on the laptop to be able to boot the USB XP hard drive.  

After reading a couple forums i set up the /boot/grub/device.map to say
hd(0)     /dev/hda
hd(1)     /dev/sda

My /boot/grub/menu.lst file says

title Microsoft Windows XP
root (hd1,0)
savedefault
makeactive
chainloader +1

When i boot up and select the Windows XP option i get the following error:

Booting 'Microsoft Windows XP'

root (hd2,0)

Error 21: Selected disk does not exist

Press any key to continue...


help please...

---

### Post by PriceChild on 2008-01-22
*moved approved and bumped*

---

### Post by torgrot on 2008-01-22
You need to use the map command in your menu.lst  Here is my entry for windows on my second hard drive.  ```

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
And here is my device map```

(hd0)	/dev/hda
(hd1)	/dev/hdb

```
and just for good measure here is the output of fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2568    20627428+  83  Linux
/dev/sda2            2569       19187   133492117+  83  Linux
/dev/sda3           19188       19457     2168775   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07066020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16709   134215011    7  HPFS/NTFS
/dev/sdb2           16710       19457    22073310    f  W95 Ext'd (LBA)
/dev/sdb5           16710       19457    22073278+   7  HPFS/NTFS

```

torgrot

---

### Post by bradhawk08 on 2008-01-24
when I changed my menu.lst file this is the error that occured:

```
Booting 'Microsoft Windows XP Home'

root (hd1,0)
  Filesystem type unknown, partition type 0x7
savedefault
makeactive
map    (hd0) (hd1)
map    (hd1) (hd0)
chainloader +1

A disk read error occurred
Press Ctrl+Alt+Del to restart
```

---

