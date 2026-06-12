---
title: "Trying to Remove Promise SATA Card"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by bobsharp on 2009-12-12
HI All, I physically removed my Promise SATA card and now Ubuntu freezes during startup. If I put the card back in everything works fine (there are no drives attached to the card). How do I remove the Promise SATA from the boot process so the computer does not freeze?

---

### Post by Fafler on 2009-12-12
The only reason i can think of is that it changes the name of the disk you use as root.

Do you have more than one disk in your system?
When you get the grub: prompt, try pressing e to edit the command line, and remove the word quiet, then press enter and b to boot. Now Ubuntu should boot without the splash image, and display boot messages instead. What is the last things it says?

Maybe grub tells the kernel to use sdf1 for root, but removing the SATA card makes it come up as sda1. Usually unused SATA ports shouldn't claim a sd? device, but weirder things have happened.

---

