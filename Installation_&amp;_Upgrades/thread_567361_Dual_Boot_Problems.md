---
title: "Dual Boot Problems"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by Thomeduk on 2007-10-04
I am trying to install Ubuntu (7.04) onto my system that comprises a 320GB SATA HDD, dedicated to WINXP, and a 80GB SATA HDD onto which I want to install Ubuntu.

I have installed Ubuntu onto the 80GB SATA HDD but when I boot the GRUB screen to allow me to select which OS to boot to does not appear.

I have 'Googled' for advice and have tried to follow most of the advice found but so far without any success, the machine will boot solely into WINXP.  I have also reinstalled Ubuntu ad nauseum. I have not yet tried the 'alternative' CD, will that help?

Please provide the solution or direct me to where I may find the solution.

---

### Post by maybeway36 on 2007-10-04
Is it booting off of the right drive? You could try installing GRUB to (fd0) if you have a floppy disk.

---

### Post by louieb on 2007-10-04
Try [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") Sounds like the installer is confused as to which hard drive is 1st in the boot order and put the GRUB pointer in the 2nd drives MBR. Did you let it put the GRUB pointer in the MBR?  More stuff here    [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

