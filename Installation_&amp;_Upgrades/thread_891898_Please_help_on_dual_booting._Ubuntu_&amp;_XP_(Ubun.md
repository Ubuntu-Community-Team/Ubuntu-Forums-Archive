---
title: "Please help on dual booting. Ubuntu &amp; XP (Ubuntu First)"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by TheFinalGent on 2008-08-16
Ok so I had ubuntu 8.04 on my laptop first then I wanted to dual boot with windows xp. I partitioned the hard drive with g parted. So it is 20gig Linux and 40gig Windows. Everything went perfectly but when I boot up my computer it immediately goes to windows. I dont see a os menu or anything it just loads xp automatically. Does anyone know what i have to do to get that menu. I really dont want to reinstall ubuntu I had a bunch of stuff on their that I dont feel like going the hell getting again.

---

### Post by ibutho on 2008-08-16
Hi,

You can use something like [Super Grub Disk]("http://www.supergrubdisk.org") to restore the Ubuntu bootloader. When you boot into Ubuntu, you would then need to edit /boot/grub/menu.lst and add an entry for Windows. Post back if you need help (include the output of "sudo fdisk -l").

---

### Post by caljohnsmith on 2008-08-16
What happened is when you install Windows, it automatically overwrites the Master Boot Record of you HDD whether you want it to or not; therefore it overwrote Grub, and you can no longer boot Ubuntu.

The Super Grub Disk that ibutho mentioned is an excellent solution, but if you don't want to go through the trouble of downloading it and want to fix it right away, you can fix your problem from the Ubuntu Live CD. Just boot the Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[should find your Ubuntu partition in the form of (hdX,Y), use that:]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then you should be all set.

---

