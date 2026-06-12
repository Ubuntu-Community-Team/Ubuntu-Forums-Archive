---
title: "Strange boot behaviour"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by bistrototal on 2006-11-28
I just re-installed Edgy after running some other distros for a few day. In the boot process, after fsck are checked out [ok], the boot process hangs. But when i press Ctrl Alt Delete it continues. But with some error messages about init rcS and init rc.6. It disappears so fast i cant actually read it. Then i'm sent to gdm.

Any idea what causing this?

Thanks,
Håvard

---

### Post by cmichaelboyd on 2006-11-28
I don't know if this is related to your problem, but I had a similar issue, and mine was because of a piece of hardware.  It was my wireless card (pcmcia), and my system would boot fine when the card was out.  I had to end up blacklisting hostap_cs so that I could load the correct driver, and all was resolved.  

Again, I don't know if this is related to your problem, but you may try removing non-essential hardware before boot and see if that helps.

cheers

---

### Post by bistrototal on 2006-11-30
> **cmichaelboyd said:**
> Again, I don't know if this is related to your problem, but you may try removing non-essential hardware before boot and see if that helps.
cheers

It disappeard after apt-get upgrade. The strange thing was that it did not occur the first time i installed it. It works at least, but i got no idea what caused it. Thanks anyway!

---

