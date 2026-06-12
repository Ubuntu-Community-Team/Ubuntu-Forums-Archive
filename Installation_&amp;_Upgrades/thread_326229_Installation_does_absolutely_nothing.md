---
title: "Installation does absolutely nothing"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by dwightr on 2006-12-27
The laptop is an Acer Aspire 3004 with an AMD Sempron.  The live CD works great; no boot problems and it finds almost all the hardware.  Hey, Ubuntu is great! :D 

But half the time the install process just seems to go away.  The machine remains responsive and does not hang.  The other half the time the install process crashes with various Python errors. :(   

Disk configuration: partition 1 - 3GB to be mounted as swap; partition 2 - 26GB windows XP to be mounted as hda2; partition 3 - 27Gb to be mounted as /.

---

### Post by taurus on 2006-12-27
How fast did you burn the CD?  You can also try the alternate CD if you want to install it on your machine.

---

### Post by dwightr on 2006-12-27
> **taurus said:**
> How fast did you burn the CD?  You can also try the alternate CD if you want to install it on your machine.
I burned the CD at the maximum speed, around 25X I think, with the tool recommended on the web site.  Maybe it is interesting that when I did a CD check from the initial menu the CD drvie ran for a while, then stopped, and there was just a blank screen.

---

### Post by ajgreeny on 2006-12-27
There's your problem, I think.  A bad CD.  Try burning the iso again at a lower speed (max x4), check the CD again, and then if all is OK try to install.

I'm interested to see your swap is hda1, rather than windowsXP.  I thought the MBR was always on the first partition of a disk, so will be interested to see if it all works as you have it. Perhaps I am wrong about the partition business - no doubt someone will put me right if I am.

---

