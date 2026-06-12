---
title: "Moved my DVD drive, now Gutsy can't fine the install disk."
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by zemlin on 2008-01-13
Config at install:
DVD drive connected to MBD IDE port.  I also have (3) CD burners on this machine.
Changed drive arrangement - now DVD drive is connected to PCI controller card.  Moved DVD drive for install because PCI card didn't seem to be able to boot from the DVD.

Gutsy sees the drive fine and I can access the install DVD, but when I try to install or update I get a message telling me to put the install disk into the drive '/cdrom/'.

It can't find the disk in it's new home.

How to I tell Gutsy that the mothership can be found at a new address?

About me:
not afraid of command line
HPUX admin experience 20 years back
just ignorant  :confused:

Moving the DVD drive back to the MBD is an option, but for reasons outside of linux, I'd MUCH rather have things as they are now.

---

### Post by chewearn on 2008-01-13
Open your software sources dialogbox (I'm not sure how to do that in Kubuntu, but it's probably somewhere in Adept).  In there, you will find the install DVD as one of the software sources.  Uncheck it, and it should stop asking you to provide the disc.

---

