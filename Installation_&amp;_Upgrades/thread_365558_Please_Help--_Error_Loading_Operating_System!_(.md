---
title: "Please Help-- Error Loading Operating System! :("
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by herbster on 2007-02-19
Hey folks, my setup is P4 2ghz, 1.2gigs RAM, ATi RADEON 9700 Pro card, and I have my drives as follows:

WD SATA 320gb (Vista installed)
Seagate IDE 40gb (XP SP2 installed)
Maxtor IDE 40gb (blank)

I downloaded Ubuntu 6.10 and installed it to the Maxtor, then I rebooted changing my boot order to the Maxtor first of course and it said "Error Loading Operating System" and just sits there.

Can someone tell me what may be wrong? Should I just download an earlier version of Ubuntu and try installing that instead? Please help :(

Thanks in advance!

---

### Post by logos34 on 2007-02-19
There's no bootloader on the maxtor...Grub probably installed to yoour seagate mbr...Boot to it instead.

---

### Post by herbster on 2007-02-19
Thank you SO MUCH! I just switched to the Seagate, booted up and saw the boot menu.. I'm in Ubuntu now! Thanks man, simple answers are the best :):)

---

