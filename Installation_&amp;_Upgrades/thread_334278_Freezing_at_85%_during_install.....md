---
title: "Freezing at 85% during install...."
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by orionMX on 2007-01-08
I am trying to install 6.10-server-amd64.  All seems to go well thru partitioning (dual with XP), and initial LAMP setup.  During final install of the LAMP files, the progress bar freezes at 85% and all system function appear to stop (no disk chatter, cd rom drive stops).  It has happened twice.  The scond time i chose not to install either dns or lamp, just hit continue to install without either program package.  Same result, a freeze at 85% complete.  ANY suggestions??  Ideas?

thanks

---

### Post by orionMX on 2007-01-08
Solved myself....

It seems that the AMD64 version has a different interface (ie. not graphical).  I tried tried the x86 desktop version and notcie that i also hanged up at 83-85%. BUT - what i also noticed with it's graphical interface was that the installer was downloading files!!!!!  After about 5-10 mins the filed were all down and the installation continued.  I am about to retry the AMD64 version again, this time gonna allow more time at the 85% point.

---

### Post by homli on 2007-03-16
Same issue here, but with 6.10-server-i386 on a machine with two Xeon dual-core procs and 2 sata drives configured in a software raid.  The pause happened at 85%, as soon as the "Installed ubuntu-standard" status message appears.  Installation continued after a bit over 10 minutes.

So, if you experience this, wait it out for several minutes and things should eventually continue.

---

