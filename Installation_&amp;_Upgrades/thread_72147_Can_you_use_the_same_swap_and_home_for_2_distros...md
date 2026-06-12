---
title: "Can you use the same swap and home for 2 distros..."
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2005-10-05
I would like to insatll anoother distro of linux along with windows.
The windows part is easy..
I was wondering if i can use the same swapo area ans home file for 2+ distros.. Or do i have to give each its own seperate ones.
thanx
If anyone has a partition sceam they would like to show ill take a look at it..

---

### Post by az on 2005-10-05
If you do not like to turn off your computer in the usual fashion, but put it into hibernation, it writes the contents of memory onto the swap.  Then, when you boot, the swap is probed and if there is an image there, it will load it into memory and resume from there.  If you use hibernation, you could not use the swap for another installation since that would screw up your saved session.

If you do not use this, then sure, you can use the same swap for different linux installations.

You can use the same home, but your mileage may vary.  I had screwey things happen when using different versions of applications and the same config files.

---

