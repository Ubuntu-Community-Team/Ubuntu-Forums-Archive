---
title: "GParted under Xubuntu 9.10 won´t format any usb drive..."
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2010-02-18
Hi,
i am running xubuntu 9.10 and can´t format any usb drive (tried few of them). The same issue i had with fluxbox mint 8 (based on ubuntu 9.10) 
I thought that my usb drives are dead, but after formatting it in windows xp, i could run from them any linux distro. I installed then mint xfce 6 (ithink based on 8.10) and crunchbang based on 9.04, and had no such issues. 

But now i am back on Xubuntu 9.10 and want to make all live usb within it.

At the end of formating process i have message something like: ```
cannot mount usb drive: The enclosing drive for the volume is locked.
```
Of course, no drive is locked. After that i can start making installation usb disk, but after some percentage it reports some error, and of course, it does not work.

Any clue?

P.S.

I have this report:

> GParted 0.4.5

libparted 1.8.8.1.159-1e0e
/dev/sdd1 als fat32 formatieren  00:00:05    ( ERFOLG )
     	
/dev/sdd1 kalibrieren  00:00:00    ( ERFOLG )
     	
Pfad: /dev/sdd1
Anfang: 62
Ende: 3853857
Größe: 3853796 (1.84 GB)
Partitionstyp auf /dev/sdd1 festlegen  00:00:01    ( ERFOLG )
     	
Neue Partitionstyp: fat32
Neues fat32-Dateisystem erzeugen  00:00:04    ( ERFOLG )
     	
mkdosfs -F32 -v -n "" /dev/sdd1
     	
mkdosfs 3.0.3 (18 May 2009)
/dev/sdd1 has 61 heads and 62 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 3853796 sectors;
file system has 2 32-bit FATs and 8 sectors per cluster.
FAT size is 3757 sectors, and provides 480781 clusters.
Volume ID is 1d199dd0, no volume label.

========================================

---

### Post by vickoxy on 2010-02-18
Yes-and when i want to unmount usb drive-it does it, but it stays always on desktop (usually usb drive icon disappears)

---

### Post by vickoxy on 2010-02-20
Bump!

Please, if anyone can help-all my USB Sticks are unusable unde xubuntu (which is my main machine). I tried to delete USB in MacOS, but i do not know is that proper solution to format USB Stick?
If i format USB in MacOs i have in xubtuntu still report that i have to format that disk (i formated it in MS-DOS FAT System). But then i have error report-something like: "you don´t have enough space to copy ISO to your disk"

---

### Post by mkvnmtr on 2010-02-20
In gparted under device there is the option to create a new partition table. Try that and then format. I have had to do that a time or two to get my sticks working.

---

