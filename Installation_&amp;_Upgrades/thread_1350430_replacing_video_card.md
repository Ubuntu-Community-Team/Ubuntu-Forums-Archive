---
title: "replacing video card"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Dave67 on 2009-12-09
This really applies to any version of ubuntu if this process is different for versions I would need to know :)

I would like to know how to fix a ubuntu system when I replace the video card to a new one once I do that gnome will not boot it load to the command shell. I figure this is do the other card video drivers installed, there are not acceleration graphics drivers installed. this is in case I find myself in the situation again I can fix it.

dave

---

### Post by darkod on 2009-12-09
These days drivers for many models are combined together so you might not need it always, but in these cases I find the EnvyNG package best.
If it allows you to start the recovery mode entry from grub (it should), select something like "root with networking" from the following menu, to have internet access.
Then when in command prompt do:
sudo apt-get install envyng-core envyng-qt

You can run it in text mode with:
envyng -t

The rest is easy. It knows where to download the driver itself (have no clue how), you just select Nvidia or ATI. It has option to remove current driver, which you might wish to do. I didn't, but my problem was different and I wasn't replacing one card with another.

Once in desktop the software is also present in Applications-System Tools (I think). It works in GUI too.

---

