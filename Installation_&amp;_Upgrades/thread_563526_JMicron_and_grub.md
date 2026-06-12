---
title: "JMicron and grub"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by stoive on 2007-09-30
I have an ECS P965T-A which i believe doesn't have a PATA controller, it uses JMicron's software to emulate a SATA drive which is all fine and well.

except that grub doesn't recognise it and giving me a Error 21 Drive does not exist.

I have my old windows installation on the PATA drive and Ubuntu on my SATA drive. While I dont care much for windows I would still like to have access to it if I need to.

Does anyone have a work around for grub apparently not being able to get the info for the PATA hdd from bios?

Should I install another boot loader that works for this ??

---

### Post by logos34 on 2007-09-30
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

You might want to post your fdisk and menu.lst:

**sudo fdisk -l **(lowercase L)

**cat /boot/grub/menu.lst**

---

### Post by stoive on 2007-09-30
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS


and bar the standard default stuff at the top here is the bit that counts in menu.lst

> title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d02f45ea-ac99-4b6c-a55e-aac354249b3b ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d02f45ea-ac99-4b6c-a55e-aac354249b3b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


---

### Post by logos34 on 2007-09-30
try:

**gksudo gedit /boot/grub/menu.lst**

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by stoive on 2007-09-30
error 21: selected disk does not exist.

so it knows that my sata drive is the 2nd hdd device, but it won't recognise my 1st hdd.

i think it has something to do with the bios reporting the PATA drive to grub

some bug with JMicron on P965T-A boards

---

### Post by logos34 on 2007-10-01
I thought the JMicron issues that plagued edgy users had largely been resolved.  Apparently not... some like you are still having [problems]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502/comments/217").

---

