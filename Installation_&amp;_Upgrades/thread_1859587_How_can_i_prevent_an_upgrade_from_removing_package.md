---
title: "How can i prevent an upgrade from removing packages?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by DylanRush on 2011-10-14
I was going to upgrade to 11.10 today from 11.04.  It goes through and calculates the changes.  I look to see what it is going to remove and find that it is going to remove the drivers for my printer.  This wouldn't be a big problem if there were 64 bit drivers for my printer.  I had to fool around trying to figure out how to force the architecture and get my printer and scanner working.  I don't really feel like having to go through this again so I wanted to know if I can prevent the upgrade from removing these drivers or not.

---

### Post by garvinrick4 on 2011-10-14
> aptitude hold pkgname: Fix a package at its current version  and don't upgrade it automatically (formerly an obscure echo-to-file  command).  unhold to remove the hold.
You would have to install "aptitude" package. This is to hold a package and not upgrade.
Have held a package before but when you say messed with your architecture using 32 bit drivers on a 64 bit system seems something you might have written down. Anyway that
is all I got, on how to hold a package.
[Your Debian Aptitude | GarfieldTech]("http://www.garfieldtech.com/blog/your-debian-aptitude") 
[FONT=monospace][/FONT]

---

### Post by DylanRush on 2011-10-14
> **garvinrick4 said:**
> You would have to install "aptitude" package. This is to hold a package and not upgrade.
[FONT=monospace][/FONT]

So your saying I would be able to hold two packages through an entire distro upgrade?

> **garvinrick4 said:**
> ...when you say messed with your architecture using 32 bit drivers on a 64 bit system seems something you might have written down.
[FONT=monospace][/FONT]

and unfortunately, I haven't written down how to do it.  In retrospect, I probably should have.

---

