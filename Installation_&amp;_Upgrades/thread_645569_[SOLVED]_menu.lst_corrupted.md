---
title: "[SOLVED] menu.lst corrupted"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by ccharoux on 2007-12-20
I loose my XP
I had a dual-boot xp/linux UBUNTU working well
I have no backup of menu.lst
Just after installing KMID my menu.lst was corrupted : entry for XP was replaced by a second entry to my Ubuntu

with gparted I see my XP partition on( hd0,0) or sda1
But I dont known the init record of it

so if I update menu.lst with  root (hd0,0) that is not sufficient to boot XP
gparted tells sector 63 is the first rec of XP

How can I rebuild my menu.lst and is my XP partition corrupted ?

Please HELP

---

### Post by PmDematagoda on 2007-12-20
Could you post the results of:-

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

---

### Post by nick_h on 2007-12-20
My grub XP entry looks like:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Is this of any help?

---

### Post by PmDematagoda on 2007-12-20
Not sure about this, but try changing:-

```
chainloader     +1
```
to
```
chainloader     +63
```

---

### Post by ccharoux on 2007-12-20
christian@Provence:~$ **sudo fdisk -l**

Disque /dev/sda: 120.0 Go, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a490b20

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2   *        2551        5101    20490907+  83  Linux
/dev/sda3            7653       14593    55753582+   7  HPFS/NTFS
/dev/sda4            5102        7652    20490907+   f  W95 Etendu (LBA)
/dev/sda5            5102        7523    19454683+  83  Linux
/dev/sda6            7524        7652     1036161   82  Linux swap / Solaris
---------------------------------------------------------------------------------------------------------
Menu.lst

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6c4276d2-8c0e-4957-bfc6-b33f3cd4265c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +63

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
------------------------------------------------------------------------------------------------------------------

I get error 13 : invalid format command, when pressing on XP line of the boot menu

---

### Post by ccharoux on 2007-12-20
YAOUH my XP is alive again !!!

Thanks a lot for your kind and fast cooperation :)

I made a mistake on menu.lst (hd0,1 instead of hd0,0)

I works fine now, may be tanks to +63 (I'll try with +1 just to see)

Thaks again !!!

---

### Post by PmDematagoda on 2007-12-20
Glad I was able to help:).

---

