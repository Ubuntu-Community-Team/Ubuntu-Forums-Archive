---
title: "Ubuntu 6.10 dual-boot problem"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by aasodi on 2006-11-01
First, sorry on my english...

I have Windows Media Center Edition 2005 installed on my home pc. I was install Ubuntu 6.10 and booting is fine. Ubuntu work very well for me, but I can't boot windows anymore. I was try to renistall windows and ubuntu, but with no luck... I have GRUB menu and when point and enter on Windows OS, screen go blank with Starting up... and cursor blinking. Nothing happens.

Please help!
Thanks in advance

Here is part of GRUB file:

title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Kateikyoushi on 2006-11-01
Could you show us your partition layout ?

Can do it with the following command.
```
fdisk -l
```

---

### Post by aasodi on 2006-11-01
This is output:

[HTML]Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      101546    51179152+   7  HPFS/NTFS
/dev/sda2          101547      117737     8160264   83  Linux
/dev/sda4          117738      484518   184857593    5  Extended
/dev/sda5          117738      119818     1048792+  82  Linux swap / Solaris
/dev/sda6          130228      484518   178562632+   7  HPFS/NTFS
/dev/sda7          119820      130227     5245600+  83  Linux

Partition table entries are not in disk order[/HTML]

Here is complete GRUB list:

[HTML]title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/HTML]

Thanks for quick replay

---

### Post by aasodi on 2006-11-02
Anybody? :(

---

### Post by j0nn0 on 2006-11-02
Can you mount your windows drive?  You may have to back it up and reinstall. I had a similar thing awhile ago, and although I could mount and read my Windos drive, I couldn't boot from it. I think the boot sector was borked somehow. I think I even tried dos fdisk /mbr.  So I had to reinstall windows from a ghost backup, then use my ubuntu cd in rescue mode to reinstall grub. Now it works, although I can't remember when last I booted windos.

---

### Post by aasodi on 2006-11-02
I can mount windows partitions. I was try fixmbr and fixboot from win cd and it works. Windows is loading, but then I don't have GRUB. I also used Super GRUB to make things right, but with no luck. Restoring grub with SuperGrub working, but then I have same problem (can't load win). For a noob like me it's nightmare (grub, sda, sectors...), but I don't give up :)

---

