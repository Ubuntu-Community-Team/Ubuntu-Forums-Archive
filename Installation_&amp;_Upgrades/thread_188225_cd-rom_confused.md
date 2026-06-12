---
title: "cd-rom confused?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by nagoogin@gmail.com on 2006-06-03
My installation hangs at while trying to mount file system.  I then receive an error that says cd-rom is confused](*,) .  If i wait long enough it just floods the screen.  My cd rom is a sony crx320E cd-burner/dvd combo drive.

---

### Post by neveceral on 2006-06-05
Hi, 
i have the same problem as you, and i have no solution too :mad: 
I tried this [http://www.ubuntuforums.org/showthread.php?t=123362/](http://www.ubuntuforums.org/showthread.php?t=123362/) 
or irqpool for booting, but all without success,
Look here [http://lists.debian.org/debian-kernel/2005/05/msg00420.html](http://lists.debian.org/debian-kernel/2005/05/msg00420.html) it is normal debian kernel bug ](*,) 
Daniel

---

### Post by neveceral on 2006-06-09
I found this out

[http://forums.fedoraforum.org/archive/index.php/t-77726.html](http://forums.fedoraforum.org/archive/index.php/t-77726.html)

[i] I've got a solution for this problem, I had the same on vanilla 2.6 kernel on RH9 and i've just fixed it on my new FC4 installation.
The problem is that default kernel has 'Sharing PCI IDE interrupts support' enabled (see Device Drivers -> ATA/ATAPI/MFM/RLL support, PCI IDE chipset options), so devices often loose interrupt.
I've just recompiled the kernel with option off, now it works ok. [/i]

but it is very very difficult (maybe impossible :-k ) for linux newbies like me ](*,)

---

