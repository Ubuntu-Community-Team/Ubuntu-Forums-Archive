---
title: "Ubuntu 11.04 failed to install Grub2 with FreeBSD partition"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ahavatar on 2011-04-29
Greetings,

I had no problem with installing Ubuntu releases in the past but Ubuntu 11.04 failed to install Grub2 with a FreeBSD partition. 

Ubuntu 10.10 (or older releases) ignored the FreeBSD partition and installed Grub2 without it, and then I manually added FreeBSD later.

But Ubuntu 11.04 tries to mount a FreeBSD partition and fails at the point and quits the installation, leaving the PC unbootable.

Is there a way to tell Ubuntu NOT TO INSTALL Grub2 at all so that I can manually install it later?

Or can we get the older version installer back for Ubuntu 11.04?

Thanks.

---

### Post by ChronoSphere on 2011-04-29
Probably not, but as a workaround you can change the FreeBSD partition's type code to something else (0x07), then install, then change it back to 0xA5.

---

### Post by ahavatar on 2011-04-30
I instead downloaded the alternatve Text based install CD, and it installs Ubuntu 11.04 fine on the same machine.

The default GUI install CD had been working fine in the past couple of years on the same machine, but suddenly from Ubuntu 11.04, it does not work any more.

I suspect that when it can't mount a FreeBSD partition (of course it can't), it just quits installation there instead of ignoring the partition and finishing the installation.

If I inspect the root partition of the failed Ubuntu 11.04 instllation, the /boot directory does not have an initrd image nor grub.cfg file, making it unbootable.

I think this is a bug, but somehow I forgot how to report a bug in the installation CD.

---

### Post by ChronoSphere on 2011-05-04
Another workaround is to boot the regular CD, and select "Try Ubuntu." Then when you are at the desktop, right-click on the "Install Ubuntu 11.04" icon, select properties, and add the "--no-migration-assistant" flag just before the "--desktop" flag. Now it won't try to mount any partitions and the install will succeed with the FreeBSD partition.

---

### Post by milstn on 2011-05-04
Many thanks it worked for me, i've lost 3 days without suspecting that this unexplained behavior from grub2 was due to the free bsd partition.did somebody posted this bug tracking system in launchpad?

---

