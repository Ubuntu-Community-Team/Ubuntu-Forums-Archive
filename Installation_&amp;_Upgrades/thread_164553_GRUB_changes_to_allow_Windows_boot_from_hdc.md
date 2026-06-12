---
title: "GRUB changes to allow Windows boot from hdc"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by wanton on 2006-04-23
Hi All,

I have looked around and found heaps of howtos but they all assume that Windows is on hda. Not sure exactly what to put in menu.lst to allow my win98 to be selected to boot. My setup up is as follows:

hda: Ubuntu
hdb: FAT32 storage
hdc: FAT32 Windows installation.

fdisk -l gives :

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Disk /dev/hda: 10.0 GB, 10005037568 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1162     9333733+  83  Linux
/dev/hda2            1163        1216      433755    5  Extended
/dev/hda5            1163        1216      433723+  82  Linux swap / Solaris

Disk /dev/hdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1216     9767488+   c  W95 FAT32 (LBA)

Disk /dev/hdc: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2501    20089251    c  W95 FAT32 (LBA)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I have tried the following but it doesn't work:

title                Windows
map               (hd0,0)(hd2,0)
map               (hd2,0)(hd0,0)
rootnoverify    (hd2,0)
makeactive
chainloader     +1

TIA

---

### Post by amohanty on 2006-04-23
How about this:

```

[B]
title             Windows
root             (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader   +1
[/B]

```

AM

---

### Post by Sutekh on 2006-04-23
I think the problem is that you mapped (hd0,0) to (hd2,0) before you set the root path as (hd2,0)

So try
```
title    Windows
rootnoverify    (hd2,0)
savedefault
makeactive
map    (hd0,0) (hd2,0)
map    (hd2,0) (hd0,0)
chainloader +1
```

---

### Post by wanton on 2006-04-23
Thanks folks, I made the suggested changes (also noticed that I didn't have the appropriate whitespace in the map commands either) and now I am <shudder> posting from MS Windows. (Still have one or two apps that I can't find acceptable linuc equivalents for)

Hopefully when I reboot into Ubuntu everything will still be fine and MS Windows won't have trashed any boot records etc.

Interestingly, I rarely boot Windows these days (previously by swapping IDE cables) but whenever I do/did it would crash at least once before the task was completed. 

No such hassle with Ubuntu (just need a wysiwyg HTML editor a-la Frontpage.....yeah, yeah I know, but it gets me going fast and I can tweak at my leisure).

---

