---
title: "Slightly strange dual boot problem"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by CamB on 2005-08-07
Hi

I've installed Ubuntu onto a second (slave) HD, leaving the existing XP one (in 2 partitions) "intact", except for what GRUB does to it (ie, I now can't just remove the second HD as XP doesn't load... I think I can fix with XP recovery, if needed).

Ubuntu loads fine, although I suck. I formatted the second drive (both are 80gb) under windows as a 55gb NTFS partition, then used the Ubuntu setup to create approx 9gb for /, 5gb for /home, a ~1gb swap file and a 5gb FAT32 file to share between the two OSs.

In the XP Disk Management utility, this drive now shows:

E: 54.53gb NTFS (a primary partition according to the utility)
9.32gb partition (this is / in Ubuntu, is ext3, and is also a primary partition according to the utility)

An extended partition, consisting of:
4.66gb partition (this is /home, is ext3, and the XP utility says its a "logical drive")
H: 5.18gb FAT32 partition (the shared Fat32 partition, which I reformatted as FAT32 under windows)
871mb partition (ie, swap)

See the attachment for a pic of the XP utility (probably better than trying to understand what I wrote, LOL).

While Ubuntu is good, the following has happened to XP:

- long wait with black screen after Windows XP splash (~45 seconds when it prob used to be 5-10 secs)
- a blue screen, which (paraphrasing, because its too long) says:

"Checking file system on .... the type of file system is FAT32. One of your drives .... needs to be checked for consistency.... Appears to be non- Windows XP...check drive for errors (Y/n)."

Pressing y or n makes no difference, and it then has "error writing log file" and, after about another 15 seconds, goes about loading XP as normal.

Short question is... does anyone know why?

I am getting reasonably close to just trying to start afresh with Ubuntu on that drive (full reformat).

---

### Post by edwina on 2005-08-07
Three things to check out ...

1) What does your GRUB file say? Look in /boot/grub/boot.lst (or something like that) and post here.

2) What does your XP boot file say? Right-click "My Computer" then advanced/'startup and recovery'/Settings/Edit and post here.

3) Can you find your error log in XP? Not sure where they go though. 

That's the best I can do, I'm afraid.

---

### Post by CamB on 2005-08-07
Thanks for helping :D

GRUB file (in short):

> default		4

timeout		10

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


XP Boot file:

> [boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

---

### Post by CamB on 2005-08-07
This might help as well --> from fdisk -l:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825        9729    47431912+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7118    57175303+   7  HPFS/NTFS
/dev/hdb2   *        7119        8334     9767520   83  Linux
/dev/hdb3            8335        9729    11205337+   5  Extended
/dev/hdb5            9619        9729      891576   82  Linux swap / Solaris
/dev/hdb6            8335        8942     4883697    b  W95 FAT32
/dev/hdb7            8943        9618     5429938+   b  W95 FAT32

Partition table entries are not in disk order
```

I see that there seem to be **two** FAT32 partitions... one of which that windows xp disk manager doesn't see. I don't remember creating it, FWIW.

Maybe that mystery partition is the problem.

Part of what is making this difficult is that I have an external USB wireless adaptor, and as the network is WPA encrypted haven't quite got network access yet. It means I have to quit Ubuntu and restart XP to reply...

---

### Post by CamB on 2005-08-08
I'm a one-man posting machine.

Rereading that partition table, is it telling me that one of my (supposedly) ext3 partitions is in fact a FAT32 at least to some extent?

It looks like hdb3 is the whole extended partition, which should be made up of 1x ext3, 1x swap and 1x FAT32. However, it's showing 2x FAT32...

---

### Post by CamB on 2005-08-08
Thanks to edwina for the offer of help - I let frustration get the better of me and:

a) ran the windows xp recovery and fixmbr (so GRUB is gone)
b) deleted the linux partitions

This "fixed" the problem.

I'm going to park my Ubuntu plans for a couple of days, then have another go :D

---

