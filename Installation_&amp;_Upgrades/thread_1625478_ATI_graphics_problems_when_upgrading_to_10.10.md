---
title: "ATI graphics problems when upgrading to 10.10"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2010-11-19
I upgraded from 10.04 to 10.10 and have lots of graphics problems. I have ATI Radeon 3200 HD graphics built into the motherboard.

How does one use the "nomodeset"?

Originally had no display, then booted to recovery mode and used low graphics, installed the "ati-driver-installer-11-x86.x86_64.run" using the sh command line from a terminal window.

But now when I try to launch the catalyst control center I get an error message,

Quote:
There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
Now Google Earth won't function at all, and I cannot logout or switch user, I have to reboot.
Any ideas?

---

### Post by sikander3786 on 2010-11-19
You won't need nomodeset parameter after driver installation.

It is recommended that you install the driver from repositories i.e, System > Administration > Additional Drivers.

But you will need to un-install the existing drivers. They come with an un-install script. Run that. Once the drivers are removed, Reboot and then install them from Repositories.

---

