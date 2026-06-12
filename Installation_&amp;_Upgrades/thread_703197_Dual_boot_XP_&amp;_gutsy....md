---
title: "Dual boot XP &amp; gutsy..."
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Amaravi on 2008-02-21
I am new to Linux and recently installed Gutsy on a second hard drive. I already had XP installed on my other hard drive but now it will not boot. I understand that this is because of the Grub Loader but I am having trouble fixing this issue. I have run 'fdisk' and received the following information:

[INDENT]Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe934e934

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9356    75152038+  83  Linux
/dev/hda2            9357        9733     3028252+   5  Extended
/dev/hda5            9357        9733     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x228b64d8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+   7  HPFS/NTFS[/INDENT]

On my BIOS the drive which has Linux is hard drive 0 (zero) whereas xp is on disk 1. As a result i opened 'sudo gedit /boot/grub/menu.lst' and entered the following which acheived nothing:

[INDENT]title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
rootnoverify (hd1,0) #(hd1,0) will be most common, you may need to adjust accordingly
makeactive
chainloader +1[/INDENT]

Thanks very much for your time.

Amaravi Z

---

### Post by forestpixie on 2008-02-21
try changing it to, alos it can cause problems using sudo with graphical apps - use gksudo instead - [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> title		Windows XP/Vista boot menu
rootnoverify	hd1,0) 
makeactive
chainloader	+1


or try
> 
title		Windows XP/Vista boot menu
root		(hd1,0) 
makeactive
chainloader	+1

---

### Post by Amaravi on 2008-02-21
Thanks for he suggestion but it still has had no effect whatsoever on my machine unfortunately.

---

### Post by gianchi on 2008-02-21
Hello Amaravi.

I'm not a Linux expert at all, but someone suggested me this program, Super Grub, for a problem I have installing Ubuntu... it didn't help me, but it seems the perfect solution for your problem. Here's the link:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by logos34 on 2008-02-21
> **Amaravi said:**
> On my BIOS the drive which has Linux is hard drive 0 (zero) whereas xp is on disk 1. As a result i opened 'sudo gedit /boot/grub/menu.lst' and entered the following which acheived nothing:

[INDENT]title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
rootnoverify (hd1,0) #(hd1,0) will be most common, you may need to adjust accordingly
makeactive
chainloader +1[/INDENT]

Since your trying to [boot windows on a second hard drive]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk"), you need to add **map commands**:

> title        Windows XP/Vista
root        (hd1,0)
savedefault
makeactive
[B]map        (hd0) (hd1)
map        (hd1) (hd0)[/B]
chainloader    +1

More info on[ this page]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows").

The file /boot/grub/device.map may also need to be changed to match.

Hope that helps.

---

