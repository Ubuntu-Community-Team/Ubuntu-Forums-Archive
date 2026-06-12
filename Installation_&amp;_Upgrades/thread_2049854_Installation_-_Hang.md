---
title: "Installation - Hang"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by RitaLoquita on 2012-08-29
I had this same issue happen with me in Fedora and I entered the launch command nouveau.noaccel=1  and everything worked quite alright.  

When I load ubuntu off of my flash drive a grub interface runs and no matter how hard I try I can't seem to properly pass the same command.  I was able to after Fedora was installed by modifying grub but this is running off a flash drive and I am extremely lazy, that takes time to redo the flash drive with persistant mem.

Anyway X Server(if its still called X Server) tends to hang during loading.  Oddly enough I can still use my mouse which seems to be documented all over.

Cpu: Corei7 3820 SB
Mobo: x79 based (Asus P9x79 Deluxe model)
---BT/Wifi Module installed
Video: Nvidia GTX 580  (seems to be the culprit in Fedora)
Mem: 4x 2gb Corsair Vengeance DDR3 1600
---4 channel config
SSD's are my main

That is really all that was installed at the time.  Since then i've added more parts but is irrelevant to my issue.  

[SIZE=4][B]TLDR Version:
How do I pass Nouveau.noaccel=1 in grub launcher.[/B][/SIZE]

---

