---
title: "Installation from USB"
date: 2024-02-20
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2024-02-20
Hi Ubuntu Community,

I'm trying to install Ubuntu from a USB that I've created, but it seems to just hang. After selecting the USB to boot from, the screen just displays my motherboard's logo (EVGA) and nothing happens afterward. 

I've tried creating the USB using Etcher and Rufus. Both give the same result. I don't know what the issue could be. 

Please help.

---

### Post by ubfan1 on 2024-02-20
Did you hashcheck the downloaded ISO?  What setting is your machine's boot type (uefi, Legacy, both (with one preferred)? When you made the install media, did you select a particular boot type, or did you keep both possibilities (like the ISO does)?

---

### Post by Shadius on 2024-02-20
Thanks for replying.

I was just able to resolve it a few minutes ago by choosing the option to boot with safe graphics.

Apparently, there was an issue with my graphics card...? Not entirely sure, but I was able to boot into Ubuntu and install it.

---

### Post by ubfan1 on 2024-02-21
Good to see you got it working. If you don't choose to install the Nvidia drivers when you first install, the first boot needs the "nomodeset" kernel option (what safe graphics does) so the nouveau driver will work. Then you can install the Nvidia drivers, and not use nomodeset.

---

### Post by Shadius on 2024-02-21
Oh, got it! Thank you for the explanation. That makes sense now.

---

