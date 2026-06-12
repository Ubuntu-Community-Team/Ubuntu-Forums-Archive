---
title: "BusyBox, kernel problem"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by Gloominati on 2008-07-08
I installed ubuntu 8.04 but when i try to boot it for first time it like gets stuck on ubuntu sign and then the busybox pops up. I tried deleting those two words with no result. I came home after a year therefore i haven't been using computer for a year and i didn't change anything, old linux 6.06 worked fine then but now during installation 6.06 error message shows that cannot create swap space and it hangs at 15% of installation. I checked CD for defects and i have ordered cd on the ubuntu webpage.

---

### Post by PmDematagoda on 2008-07-08
When you reach the GRUB menu, press "E" at the entry for Ubuntu and then at the kernel line press "E" again, then go to the end of the line and remove the words "splash" and "quiet" and press Enter, then try booting Ubuntu again by pressing "B" and see if there is an improvement.

---

### Post by Gloominati on 2008-07-08
i have tried that, it says something with CD-drive.

---

### Post by PmDematagoda on 2008-07-08
> **Gloominati said:**
> i have tried that, it says something with CD-drive.

Did you try removing the CD-Drive and seeing if Ubuntu boots up properly with that? If it works then it may either be something with the driver for the CD-Drive or the CD-Drive itself.

---

### Post by Gloominati on 2008-07-08
Alright i will try that. Otherwise everything works, live cd and i do not get how it could affect loading OS.

---

### Post by Marlo_nl on 2008-07-08
Gloominati,

How much partitions does your hard drive have?

In case you have more than 15 partitions, installation of Ubuntu 8.04 will probably fail as it did for me.


Regards, Marlo

---

