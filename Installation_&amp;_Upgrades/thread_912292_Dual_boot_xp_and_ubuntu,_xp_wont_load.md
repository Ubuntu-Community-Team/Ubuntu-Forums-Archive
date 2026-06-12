---
title: "Dual boot xp and ubuntu, xp wont load"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by burton247 on 2008-09-06
hi, i was hoping for some input
Basically i have windows installed on  sata hard drive and tried installing ubuntu hardy on an ide drive.
the install went fine and grub had both ubuntu and windows listed but neither would boot. I ran sudo fdisk -l and saw my hard drives werent right in menu.lst so i changed them to what i thought was correct. ubuntu works fine now but when i select windows it just hangs, doesnt post an error, just hangs. 

sudo fdisk -l gives this output
```
burton@burton-desktop:~$ sudo fdisk -l
[sudo] password for burton: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031141

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6225    50002281   83  Linux
/dev/sda2            6226       38913   262566360    5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
/dev/sda6            6226       38536   259538044+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe50d568a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25179   202250286    7  HPFS/NTFS
/dev/sdb2           25180       30401    41945715    f  W95 Ext'd (LBA)
/dev/sdb5           25180       30401    41945683+   b  W95 FAT32

```

my device map file is 
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

finally part of my menu.lst
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=becd6269-7d76-4ebe-8be5-d295fdaff13f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=becd6269-7d76-4ebe-8be5-d295fdaff13f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

can someone please help cause i cant figure out whats going wrong, it worked fine from install with mandriva so i know it can be made to work easily but im unable to see whats wrong

thanks

---

### Post by caljohnsmith on 2008-09-06
Try changing your Windows entry as follows and I think you will be fine:
```
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
[COLOR="Blue"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader	+1
```

---

### Post by burton247 on 2008-09-06
no luck :(
still hanging with "starting up" on screen
tried disconnecting my ubuntu hard drive and its still trying to load grub :S
not sure what ive done cause it used to load windows when i did that

---

### Post by caljohnsmith on 2008-09-06
> **burton247 said:**
> no luck :(
still hanging with "starting up" on screen
tried disconnecting my ubuntu hard drive and its still trying to load grub :S
not sure what ive done cause it used to load windows when i did that
So you are sure Ubuntu boots fine when you use (hd0,0) in its menu.lst entries? That means you are booting off the Ubuntu HDD. When you disconnect the Ubuntu HDD and get a Grub error on start up, that means Grub is also installed in the master boot record (MBR) of your Windows HDD. If you want to restore your Windows MBR so you can boot Windows when the Ubuntu HDD is disconnected, just boot your Windows Install CD and run the command "fixmbr" with your Ubuntu HDD disconnected. If you don't have a Windows Install CD, there are other ways of restoring its MBR; let me know if you need more info on that.

---

### Post by burton247 on 2008-09-06
yeah sorry, i forgot to save menu.lst i think
anyway, i did it again and yeah it works fine
yeah i thought that had happened, i dont have a windows disk, but ill have a look myself for restoring the MBR, not a major problem 

thanks for you help and sorry for messing it up the first time

---

