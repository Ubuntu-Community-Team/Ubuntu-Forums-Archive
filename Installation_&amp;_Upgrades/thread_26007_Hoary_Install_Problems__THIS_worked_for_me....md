---
title: "Hoary Install Problems ? THIS worked for me..."
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by iminj on 2005-04-11
I've been watching the Forum since April 8th, and have noticed that the number of unresolved installation woes is growing. Here's how I overcame problems.

I have an older limited resource system:
Pentium II - 266MHz
192 Mb RAM
Nvidia - RIVA 128

Warty has been on this system for 5 months. I decided to NOT dist-upgrade to hoary - because I had non-standard repo's, backported packages, and a few locally compiled packages. It made more sense (so I thought) to download the new hoary 5.04 .iso, and do a fresh install.

What followed was 4 days of frustration and 5 or 6 failed installations: ...... Stalled installation, Kernel Panic, x.org failing to load, Broken ubuntu-desktop, and Gnome desktop app's failing to load. I have a new collection of cd-coasters because someone convinced me my CD had corrupted files ..

FINALLY, I found a workaround:


(1) Installed **Warty** from my original CD

(2) Went into synaptic (in warty) and upgraded all packages to bring it all up to date. I didn't install, edit, or modify anything else.

(3) Shut down and rebooted into warty (Probably not necessary - but I wanted to be sure it would)

(4) Went back into Synaptic. I disabled the First repo (warty CD) and then I changed all warty references to **hoary** in _all other active _ repositories. I didn't activate universe repo's.

(5) Still in Synaptic, I upgraded (smart upgrade) 

After an hour, I was finally able to boot into hoary without all the prior problems. I hope this helps someone ...

-iminj

---

### Post by fng on 2005-04-12
I have the same problems on a PII 333.

other symptons i encountered : 
- unable to find the cdrom in the middle of the installation
- unable to install extra packages
- 

Gonna try your solution this evening
Hope it works

---

