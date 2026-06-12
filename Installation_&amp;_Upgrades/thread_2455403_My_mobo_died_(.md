---
title: "My mobo died :("
date: 2020-12-18
forum: Installation &amp; Upgrades
---

### Post by pengyou2 on 2020-12-18
When I get my new one I am going to do a new install of Ubuntu.  The new computer will include m.2 memory and 2 video cards.  Will the hard drives from my old computer be locked - because I did not have time to prepare them for being uninstalled?

---

### Post by Autodave on 2020-12-18
If all that is on them is Linux, you won't have an issue with them being locked.  If there is Windows on any of them, that may or may not be a prob.  You can buy an external connection to run them through a USB port.  Doing that will let you know whether they are locked or not.  If they are, then you need to borrow someone's Windows machine, set the BIOS to shut down and not hibernate, and connect the HD to that machine and power it down.  Then, it should be unlocked if you disconnect them before power the Win machine up again.

---

### Post by kansasnoob on 2020-12-19
The biggest problem I've encountered in such a situation is if the new mobo is UEFI and the old mobo was not. In that case there is no real option other than to start with a fresh install and transfer all of your old data using the appropriate drive connections which could vary greatly depending on hardware. If the drive was encrypted that would certainly open a whole other can of worms.

A much more minor issue is difference in graphics chips but that should be easily worked around by booting using the "nomodeset" boot option so you can sort out the graphics driver issue from the desktop.

---

### Post by Impavidus on 2020-12-20
> **kansasnoob said:**
> The biggest problem I've encountered in such a situation is if the new mobo is UEFI and the old mobo was not.

Even in that case the only problem is that you can't boot from your hard drives. You can still access them to backup any files you need. But in most cases, you can just plug the hard drive onto the new motherboard, replace CPU, memory, whatever changes and your system still boots. There are cases of new hard drives not working with old mobos, but I never heard of an old harddrive not working with a new mobo (or it must be prehistoric).

---

### Post by thomasrjohnson on 2020-12-20
Try to boot it, I take my drive from work and slap it into my laptop at home almost nightly. The first time I had some hardware stuff to set up but now it's fine in either machine.

---

