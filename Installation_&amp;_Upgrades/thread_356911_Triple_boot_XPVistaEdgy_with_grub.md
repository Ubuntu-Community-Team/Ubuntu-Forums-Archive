---
title: "Triple boot XP/Vista/Edgy with grub"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by MadMasta on 2007-02-08
The other day I picked up a version of Vista, installation when fine but now I can't seem to get it to triple boot.  I didn't do anything to my XP partition and I didn't change anything on grub but that partition won't boot.  I have my Ubuntu on /dev/hdb1, my Windows XP on /dev/sda1 and my Vista on /dev/sda2.  My current grub/menu.lst looks like...

```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Windows XP
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	(hd2,0)+1

title 		Windows vista
root		(hd2,1)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot
```

Thanks!

---

### Post by chipmonk010 on 2007-02-08
try adding:

savedefault

under the vista section right above make active like this:
title 		Windows vista
root		(hd2,1)
savedefault
makeactive
chainloader	+1
 
make sure root is pointing to the correct partition

---

### Post by chipmonk010 on 2007-02-08
on second read looks like there both not working:

title		Windows XP
root           (hd0,1)
makeactive
chainloader  +1

title 		Windows vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1

try replacing the two windows entries with that

---

### Post by confused57 on 2007-02-09
I'm not familiar with the entries to boot Vista, but you probably need the same mapping commands that you have for XP.  Also, you may need to hide XP & Vista from each other, as described here:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

scroll down a page or two & you'll find the info for (un)hiding.

---

### Post by MadMasta on 2007-02-09
Thank you, it's working now.

---

