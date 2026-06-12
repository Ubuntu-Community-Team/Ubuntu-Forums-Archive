---
title: "Grub/MBR problems"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by Craleu on 2007-09-24
Hello, I have a problem with installing ubuntu on my thumbdrive and now my computer wont boot with out the jumpdrive plugged in i was wondering how to fix this problem.

So it seems my problem is with my  MBR i was wondering if anyone could assist me in my problem of fixing it, the problem was caused by installing ubuntu on my thumdrive. now the computer will not boot with out the jumpdrive being pluged in, i'm
 assuming it changed the MBR to look at the jumpdrive 1st. i was wondering if anyone could assist me in f ixing this problem thank you

---

### Post by Pumalite on 2007-09-24
for anyone who may wish to do exactly what i did. The easiest was that i have found is to physically disconnect all other hard drives.. Then boot from the Live CD and install on the USB hard drive using the guided partition. This was you are 100% you are only installing on the USB hard drive and the install is not trying to get space from C: drive as i found it was... Then modify you BIOS to allow for boot from usb before the internal hard drive.. Once installed reconnect any other hard drives and your good to go...

You can restore the XP MBR with install CD>hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by Craleu on 2007-09-24
what install CD? Ubuntu? explain please

---

### Post by Pumalite on 2007-09-24
I was assuming you had XP in your system and you had lost access to it. Is that so? If yes, then: XP CD.

---

### Post by Craleu on 2007-09-25
i am unable to get the install cd to work because i get the  grub error soon as my dell logo goes away

---

### Post by Pumalite on 2007-09-25
You have to set your BIOS to boot from CD.

---

