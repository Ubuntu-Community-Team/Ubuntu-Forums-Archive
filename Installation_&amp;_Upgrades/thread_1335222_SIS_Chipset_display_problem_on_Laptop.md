---
title: "SIS Chipset display problem on Laptop"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Terrytalk on 2009-11-23
I am a New User and have just installed Ubuntu 9.10 to my laptop as a duel boot with XP, having previously made a successful FULL installation  of 9.10 to my Desktop.
Unfortunately my laptop has a SIS VGA Chipset which is causing serious display problems psycodelic flashing lines and colours. Consequently I need to remove Unbutu from my laptop restoring the original XP single boot setup. Can anyone assist please.
Cheers

---

### Post by Mark Phelps on 2009-11-23
You will need to do the following:
1) Boot from Ubuntu LiveCD and use the Partition Editor to remove the Ubuntu partition
2) Use the same tool to expand the XP partition to fill the unassigned space
3) Boot from an Win XP CD into a command line and run fixmbr -- to restore the MBR.

See the link below for assistance in step 3) :

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/]("http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/")

---

