---
title: "[SOLVED] Another GRUB problem after installing XP"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by bmwman on 2008-10-06
I've had my HTPC running Ubuntu for a while now. I have it connected to my 50" TV and I wanted to play some of my favorite PC games. I tried  making  them run with WINE and some work but some don't. So finally I decided to install XP just so I can play games. I was aware that it would overwrite GRUB and there is a way to fix it. After the XP install completed, I used the Super Grub from within windows and I got the Grub back on. So i'mm back to Ubuntu  but XP is not listed. I tried adding it manually to the grub menu.lst but i keep getting error 22 when try to launch it.

here is my sudo fdisk -l output:
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfee0c03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            1238       60801   478447830   83  Linux
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0cded2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         365     2931831   82  Linux swap / Solaris
/dev/sdb2             366       30105   238886550   83  Linux
/dev/sdb3   *       30106       36481    51215220    7  HPFS/NTFS

And here is what I added in /boot/grub/menu.lst

> title Microsoft Windows XP Professional
rootnoverify (hd1,2)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot

So XP is installed on sdb3 which should be hd1,2 but it doesn;t work.

So what is wrong?

---

### Post by bmwman on 2008-10-07
I  tried changing this line > rootnoverify (hd1,2). I tried (hd0,2) and then it seems like windows is trying to load but it just get messagin "Starting up" and  sits there. It never loads anything. If I change it back to (hd1,2) which I think it should be the right on, Grub error 22, partition doesn't exist or something like that.

Little help pls?

---

### Post by caljohnsmith on 2008-10-07
Try this and let me know what happens:
```
title Microsoft Windows XP Professional
rootnoverify (hd0,2)
chainloader +1
```

---

### Post by bmwman on 2008-10-07
That worked!!! You are the man.

Thank you.

---

### Post by caljohnsmith on 2008-10-07
No problem, glad it worked. Cheers and have fun. :)

---

