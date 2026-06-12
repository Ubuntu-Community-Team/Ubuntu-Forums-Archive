---
title: "[SOLVED] dual-boot ubuntu 8.04 and XP grub prob"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by swankish on 2008-10-21
I recently created a partition for XP in order to run some programs i wanted to run and the creation and installation went well.  However, when i restored my GRUB, i cant get onto my XP partition anymore.  It gives me Error 21: Selected disk does not exist.  I think the fact that BOTH partitions are on the same HD, as I only have one, has something to do with it.  can anyone help?

Here is my sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    94542524    47271231   83  Linux
/dev/sda2   *    94542525   153308294    29382885    7  HPFS/NTFS
/dev/sda3       153308295   156296384     1494045    5  Extended
/dev/sda5       153308358   156296384     1494013+  82  Linux swap / Solaris

---

### Post by louieb on 2008-10-21
Please post the windows entry from /boot/grub/menu.lst.
it should look someting like this.
```

title        Microsoft Windows XP Professional
root        (hd0,1)
makeactive
chainloader    +1


```

---

### Post by swankish on 2008-10-21
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1


I actually have 2 like that haha.  It looks like the second one is completely wrong because i dont have a second HD
I think i maybe set it to a nonexistant hardrive? should it be (hd0,?) maybe (hd0,2)?

---

### Post by swankish on 2008-10-21
I deleted what i had and put what you responded with and i think its fixed
thanks a bunch

---

### Post by louieb on 2008-10-21
Good to see you got it working again.

---

