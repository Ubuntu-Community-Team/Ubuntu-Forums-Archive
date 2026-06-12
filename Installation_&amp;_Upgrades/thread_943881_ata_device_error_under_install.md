---
title: "ata device error under install"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by SM411 on 2008-10-10
Hi.
I have been using ubuntu and winxp in dualboot for a long time. But i manage to break my motherboard and i bough a new one. But the problems start afer I have installed this motherboard. When I tried to install ubuntu I got some errors. I thought it was just my motherboard that was not compatible with ubuntu and i hoped that that would be fixed in the next version. But now that i got the new version (beta), I see that there is no difference. I still get the same errors. And dont tell me to try another CD, because i have tried 4different CDs. I have also tried to install inside xp but then i get the errors when i try to boot from the instalation.

The error i get is this:
ata1: softreset failed (device not ready)
ata2: softreset failed (device not ready)
Picture of the errors:
[[IMG]http://bildr.no/thumb/268776.jpeg[/IMG]](http://bildr.no/view/268776)



Since it refered to someting called ata, I just thouht it might be one of my hdd's that was broken. So i disconected one by one. I tried to disconect all but not anything helped. So its not any of my hdds thats broken.

What do you think it could be that make these errors, and can it be fixed? I dont wanna stop using ubuntu.

Btw, i tried opensuse and that worked 100%.

---

### Post by SM411 on 2008-10-11
Bump

---

### Post by qwertymodo on 2008-10-14
try adding the all_generic_ide parameter to your kernel boot (use f6 on the boot menu).  alternatively, elsewhere on the forums you'll hear a lot about switching your SATA from IDE to AHCI, but don't, cus that doesn't play nice with XP

---

### Post by SM411 on 2008-10-14
Thank you, gona try it when i come home.

---

