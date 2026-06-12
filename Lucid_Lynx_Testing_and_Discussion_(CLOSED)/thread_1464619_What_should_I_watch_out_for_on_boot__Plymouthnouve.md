---
title: "What should I watch out for on boot?  Plymouth/nouveau question"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by qyot27 on 2010-04-28
I'm asking this now so I don't have to worry about it tomorrow.

I have a GeForce 6200 PCI card, and I know that problems with Plymouth are reported for Nvidia cards.  Additionally, I know about nouveau being available by default now.

I previously have tried both Alpha 3 (via LiveCD) and Beta 2 (via Wubi, which I don't use if I don't have to), and I always got stuck on the boot splash, and the computer would just go silent at that point.  I also experienced this trying out Beta 2 on my grandparents' computer, again through Wubi (it has a VIA chipset, which I know also is reported to have issues).

I had tried to install nouveau in 9.10, but I recall having problems with it and I just went with the proprietary ones instead.  I know that all three of those can be installed side-by-side in 10.04 with only one activated, but if I have problems dealing with nouveau again, I want to know what my options are.


So what I want to know is, are these resolved in the RC or if not, by the Final Release?  If not even then, are those two things going to mess with booting into the installer/LiveCD, and will I need to manually enter the overrides every time I try to boot into 10.04, or is there a way to store those settings permanently?

---

### Post by garyedwardjohnston on 2010-04-28
i wouldn't anticipate problems

tomorrow boot from the live cd and go from there

---

### Post by elkikin on 2010-04-28
Plymouth works fine with Nouveau (the open source driver for NVIDIA cards). With the closed source drivers, it's a hole different story. You'll end up with a butt ugly 640x480 splash.

There is a workaround, but I hope this issue gets resolved soon... Otherwise, why use Plymouth in the first place? People need the closed source drivers to get Compiz and 3D working.

---

### Post by qyot27 on 2010-04-28
> **garyedwardjohnston said:**
> i wouldn't anticipate problems

tomorrow boot from the live cd and go from there
Of course, I just want to be prepared and know what to do immediately (or at least know what to search for when looking it up) and not spend hours hunting down a solution if it doesn't work smoothly like previous versions have.

[quote=elkikin]Plymouth works fine with Nouveau (the open source driver for NVIDIA cards). With the closed source drivers, it's a hole different story. You'll end up with a butt ugly 640x480 splash.

There is a workaround, but I hope this issue gets resolved soon... Otherwise, why use Plymouth in the first place? People need the closed source drivers to get Compiz and 3D working.[/quote]
It wasn't really a question about Plymouth interacting with Nouveau, it was about each individually against my hardware.  I saw posts that the freezing or unresponsiveness during boot was due to Plymouth and Nvidia-based cards in general, I didn't think it was related to the driver being used (and I'm not really concerned about how good/bad the boot splash looks, so long as I can actually get to the desktop without problems...which I wasn't able to do with either of the 10.04 testing versions I've tried).  I'm not altogether sure how much support my particular card has in Nouveau - although, seeing as it's a five year old card, I would assume the support is pretty good...the 6200 isn't exactly bleeding edge technology.

---

### Post by sgage on 2010-04-28
I have a GeForce 8500 GT card in a computer that is now probably considered quite below average (Pentium dual-core at 2 GHz), and it works fine with the proprietary nvidia drivers. The boot screen was indeed a bit ugly, but a simple workaround takes care of that. My entire boot process takes about 20 seconds.

Lucid is very nice for me, and I'm glad that it's an LTS release.

---

