---
title: "corrupt dpkg status file"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by duzinga on 2011-10-16
I tried to upgrade from 11.04 to 11.10, and the upgrade failed due to errors in my dpkg status file. I tried replacing the status file with every backup available on the system to no luck. 

I had this problem before when I was installing some packages in the system, but repeated executions of ```
apt-get -f install
``` and ```
dpkg --configure -a
``` would solve the problem. This time the system failed to no rescue, so I wiped it clean and tried to install a new OS. Ubuntu 11.10 failed to install both from CD and USB. I tried Kubuntu 11.10 which installed successfully, but now I still have the problem with corrupt dpkg status file. Every time I install a package the status file is corrupt most often with spaces replaced with quotation marks ("). On top of this the Kubuntu installation I have at the moment is very unstable, with programs crashing for no reason.

I have run Memtest86+ and no errors were found.

Any ideas what could be causing all this?

I'm installing the 64bit versions on a DELL Latitude E5510 laptop.

---

