---
title: "&quot;Failed to Load Operating System&quot;"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by Ashiro on 2006-08-20
Well I decided to jump on the Ubuntu bandwagon but hit a brickwall straight after installation.

I get the message:

"Failed to Load Operating System"

And then it hangs.  No details, no information, no help.

I've had issues with other distro's because I have an nForce3 250 motherboard which Grub and LILO seem to have issues with due to the SATA controller.  However, I've never had anything like this.  I did a search on Google to no avail so if anyone had any ideas then I'm all ears.  I'd really like to find a distro that doesn't make me rage with frustration.

**System Information:**
AMD Athlon64 3000
nVidia nForce3 250 motherboard (Gigabyte).
ATI Radeon 9800 Pro.

---

### Post by Rez. on 2006-08-20
It sounds like your Ubuntu installation has set it's partition as active and GRUB/LILO has been installed to your Ubuntu root instead of the MBR. One way to see if this has happened is to boot using something like [SysrescCD]("http://www.sysresccd.org/Download"). Boot using this CD and run QTparted and see which of your partitions has been set to active. If you find your XP installation is not set to Active, Set it to active and commit. Exit and reboot and you should boot into XP.

---

