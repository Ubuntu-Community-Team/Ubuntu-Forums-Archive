---
title: "Booting from second HD"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by Doc P on 2006-12-12
I'm very new to Linux, but experienced Windows user. I managed to intall Kubuntu on my system (ASUS PB5 deluxe mainboard, 2 SATA HDs) on second HD (root partition ext3, swap partition linux swap, additional fat 32 partition). I installed the Grub boot loader also on second HD. Now I can boot Kubuntu, but only if I disconnect the first HD on my mainboard. If I leave the first HD connected and use the BIOS Boot menu to boot from second HD Kubuntu will only boot to a BusyBox Built-in shell (ash) saying:
/bin/sh:can't access tty; job control turned off (initrams)
Any ideas for a solution without touching my first HD (which contains Windows XP)?

---

### Post by aysiu on 2006-12-12
There's nothing wrong with installing Grub to the Master Boot Record. In fact, that's probably the easiest solution, as Grub 9 times out of 10 will automatically add Windows to the boot menu.

Windows, however, 0 times out of 10 will add Kubuntu to the boot menu.

---

### Post by Doc P on 2006-12-12
Thanks,
but for some reasons (e.g. planning to install Vista on second Partition of 1st HD) I want to leave the fist HD untouched.
Booting the installed version from floppy or CD would also help but I don't know how I can create such a boot medium.
If there is no other possibility I will stick to disconnecting the first SATA HD when using Linux (Kubuntu 6.10).

---

### Post by aysiu on 2006-12-12
You could try this:
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

---

### Post by Doc P on 2006-12-12
Thanks,
for now I was successful with "Super Grub" Floppy using item "direct Linux boot".
Unfortunately it takes quite a long time and the CD Version will not work correctly.

Meanwhile, with the help of Super Grub I found the final solution.
Just had to edit the menu.lst, the line with kernel pointed to the wrong hd(a), had to be hdb.

---

