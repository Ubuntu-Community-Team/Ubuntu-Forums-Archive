---
title: "Dramas with SATA hard drive"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by coffeenazi on 2006-09-23
Hi folks, 

Mum’s pc is Ubuntu-bound after long & irreparable issues with Windows XP. I am trying to install onto a new Western Digital SATA hard drive and, of course, things are not going smoothly. I can't get into the partitioning stage of installation, and I suspect the following is the culprit...

This ASUS A8V-MX motherboard was previously set up with an IDE hard drive running Windows... now the BIOS won't recognise the new SATA drive and all of the available solutions I can find are aimed at Windows users, not newbie Linux converts like me.

I have tried to update the BIOS with the utilities from ASUS but the instructions are for using with a DOS prompt, the commands don't work on the Ubuntu terminal that I can get going from the Live Install CD.

Thanks in advance...

---

### Post by robio376 on 2006-09-24
Try to access the bios and look for anything about ide or sata. I have a asus motherboard also and it was originaly used with ide drives till I upgraded. I had to play around with the bios to get the boot sequence to recognize them. Also if you have any other hard drive connected via ide, you might want to try to unplug them and just use the sata drive.

---

