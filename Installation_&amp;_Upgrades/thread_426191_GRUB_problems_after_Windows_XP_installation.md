---
title: "GRUB problems after Windows XP installation"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by bravemosquito on 2007-04-28
This is my **/boot/grub/menu.lst**:
```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b6d3b6a7-c03c-4bda-a16c-7ba865ee259b ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b6d3b6a7-c03c-4bda-a16c-7ba865ee259b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
```

After Win XP installation GRUB was changed with MS bootloader. Hopefully I have a Super GRUB disk with which I recovered GRUB. Now Feisty boots but every time when I put a section for Windows boot option (between memtest86+ and recovery mode), save **menu.lst** and restart the pc this option is missing. OK, I boot in Ubuntu and found that the new section is not saved :-k 

Any help will be appreciated

Edit: This is my partitions, the hdd number is correctly typed by me (hd0,1):
```
root@dontouch:~# fdisk -l

Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12748   102398278+  83  Linux
**/dev/hda2           12749       17847    40957717+   7  HPFS/NTFS** <= hd0,1
/dev/hda3           25417       25607     1534207+  82  Linux swap / Solaris
/dev/hda4           25608       30515    39423510   83  Linux
```

Edit2: Searching in forums I realized that my way is wrong. Now I just write section not between Ubuntu and memtest86+, but after last line:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows XP
rootnoverify (hd0,1)
savedefault
#makeactive
chainloader +1
```

But still I cannot boot the XP :?

---

### Post by louieb on 2007-04-28
Probably something simple like uncommenting the makeactive line.
```
# this is a comment
#makeactive
#change the above to this
makeactive
```

---

### Post by bravemosquito on 2007-04-30
OK, now I'm back in business :mrgreen: 
I found what's causing the issue - the Windows partition was hidden.
**louieb**, I can boot Windows without uncommenting **makeactive** line :-k

---

