---
title: "kernel offset disabled kernel panic not syncing VFS unable to mount root fs on unknow"
date: 2016-08-10
forum: Installation &amp; Upgrades
---

### Post by shompol2 on 2016-08-10
**kernel offset disabled kernel panic not syncing VFS unable to mount root fs on unknown-block(0,0)**

Hardware: MSI all-in-one 24GE 2QE-015US
Disk: Kingston SSD V300 240GB SATA III SV300S37A/240G

Previously I was running a Cinnamon XFCE distribution. I had some issues installing it as well (probably the same one), a solution was to run under full HD encryption.
1. Made Ubuntu 16.04.01 live disk
2. Booted into live mode -- it did not detect that I had a system installed
3. Started default install
4. After reboot: [B]kernel offset disabled kernel panic not syncing VFS unable to mount root fs on unknown-block(0,0)
[/B]
I cannot boot from HD. When I boot from live USB it pops a menu, selecting anything off that menu: 
"Try Ubuntu"  --> **kernel offset disabled kernel panic not syncing VFS unable to mount root fs on unknown-block(0,0)**
"Install Ubuntu" --> **kernel offset disabled kernel panic not syncing VFS unable to mount root fs on unknown-block(0,0)**
"Check disk" --> **kernel offset disabled kernel panic not syncing VFS unable to mount root fs on unknown-block(0,0)**
"Boot from first hard disk" --> 
```
Booting from local disk...
Boot Error
Error: attempt to read or write outside of disk 'hd0'
Entering rescue mode...
grub rescue>

grub rescue> ls
(hd0) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos1)
grub rescue> ls (hd0)/boot
error:unknown filesystem
. . .
grub rescue> ls (hd0,msdos1)/boot
Error: attempt to read or write outside of disk 'hd0'
```


So Live USB is pretty useless. It even says so in Help: "There is no dedicated rescue mode on this disk."

---

### Post by Alexander_Sviridov on 2016-08-23
Try holding 'c' when the liveCD is booting. Just had this problem with Ubuntu 16 on Toshiba Satellite.

Hold 'c' it should load language menu.

---

