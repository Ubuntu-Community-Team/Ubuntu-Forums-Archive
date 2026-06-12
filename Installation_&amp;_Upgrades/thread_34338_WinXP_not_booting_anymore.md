---
title: "WinXP not booting anymore"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by petesmc on 2005-05-14
[SIZE=7]FIXED - Solution in next post[/SIZE]

Hi,

I installed (k)ubuntu the other day and since i can't get Windows XP to boot. If i select WinXP in the grub bootloader, it gets to the WinXP loading screen, howver it attempt to do a disk check but comes up with an error:

autochk not found

So, i tried to do what someone recommended, in loading XP install Cd and running 'fixmbr'. This effectively deleted grub in the mbr and tried to load WinXP only. It didn't work. Same issue. However, when running the restore console in WinXP install cd, i noticed something:

When it asked to choose my installation, it gave me one option:

**E:\Windows**

I installed on **C:\**. So i'm guessing something is messed up with my partitions, hence why it can't find anything, because it's on C:\.


Here's my fdisk -l:

```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+  17  Hidden HPFS/NTFS
/dev/hda2            2433        3568     9124920    f  W95 Ext'd (LBA)
/dev/hda3            3569        4799     9888007+  83  Linux
/dev/hda4            4800        4864      522112+  82  Linux swap / Solaris
/dev/hda5            2433        3568     9124888+   7  HPFS/NTFS

```

And here is my partman log: [partman log](http://www.ubuntuforums.org/attachment.php?attachmentid=1072) 

Can anyone figure out how to restore this, it's vital???


-Peter

---

### Post by petesmc on 2005-05-14
[SIZE=7]FIXED[/SIZE]

Solution: 

sudo fdisk /dev/hda
t
1
7

t (Change id code)
1 (partition 1)
7 (ntfs)


The problem was somehow it got changed to hidden ntfs which screwed everything up. Now it's up and running!

---

### Post by telmo on 2005-05-14
DAMN IT! I was about to congratulate you... eheh

---

### Post by gosh on 2006-02-13
Hi, 
I have the same problem. When I tried your solution I got:

```

$sudo fdisk /dev/hda1

The number of cylinders for this disk is set to 7011.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): t
Partition number (1-4): 1
Hex code (type L to list codes): 7
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

---

### Post by gosh on 2006-02-13
I fixed it by changing my /boot/grub/menu.lst

```
title		Microsoft Windows XP Professional
unhide 		(hd0,0)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

