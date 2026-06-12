---
title: "System freezes during normal boot"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by MechWarrior001 on 2012-08-04
I've been tasked with restoring an old Compaq for use; Installing via the alternative installer works fine but the system cannot seem to boot; It freezes during the Lubuntu splash screen.

The tower uses a Socket 754 motherboard with a SiS IGP chip-set. It came stock installed with a Sempron 3100+ which I replaced with a spare Athlon 64 3200+ I had stored away.

For the most part everything checks out (which is making me wonder what is causing the problem); However there does seem to be a slight problem with the BIOS: It thinks it has more RAM installed than there physically is. As of the current moment there are 1536MB of DDR400 RAM installed in the system, however the BIOS thinks it has upwards of 9216MB available for use.

Now I'm unsure how Linux determines the amount of RAM available for use (Does it read from the BIOS or does it count the RAM manually?) but could this possibly be causing the freezing during standard boot-up?

---

