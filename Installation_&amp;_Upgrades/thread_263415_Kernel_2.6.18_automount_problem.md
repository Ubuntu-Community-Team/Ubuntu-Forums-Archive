---
title: "Kernel 2.6.18 automount problem"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by emuman on 2006-09-23
Hi,

I'm using 6.06 with kernel 2.6.17. After upgrading to 2.6.18 automounting of usb devices in kde (usb sticks, usb harddisk, MMC in card reader) doesn't work anymore. Kernel 2.6.17 with the same configuration or the ubuntu kernel 2.6.15-23  works fine. Is there any known compatibility issue with ubuntu 6.06 and kernel 2.6.18? Maybe a d-bus problem?

---

### Post by Monsieur Gonzalez on 2006-09-26
Same here. I've searched the forums but found no answer. I sure hope someone finds out :)

---

### Post by David Corrales on 2006-10-29
Same thing here. Looks like we're missing some configuration somewhere =/
CD automounting is gone too.

---

### Post by Wheelman on 2006-10-29
> **emuman said:**
> Hi,

I'm using 6.06 with kernel 2.6.17. After upgrading to 2.6.18 automounting of usb devices in kde (usb sticks, usb harddisk, MMC in card reader) doesn't work anymore. Kernel 2.6.17 with the same configuration or the ubuntu kernel 2.6.15-23  works fine. Is there any known compatibility issue with ubuntu 6.06 and kernel 2.6.18? Maybe a d-bus problem?

I am running 6.1 and have lost automounting for my sd/mmc card with the kernel upgrade to 1.6.17-10 as well.  If I load it with 2.6.15-27 in grub, then it works just fine.  I really wish I could find a solution!!:-k

---

### Post by David Corrales on 2006-10-30
What I did was recompile the Ubuntu kernel with the extra options I wanted (specific processor, 1000mhz interrupts) and it's working ok. I lost the ability to suspend while using fglrx -which worked under 2.6.18- but I need automount.

---

### Post by Canadia on 2007-01-03
After upgrading to kernel 2.6.19 I lost automount as well,

---

