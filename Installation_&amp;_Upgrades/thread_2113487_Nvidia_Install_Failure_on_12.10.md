---
title: "Nvidia Install Failure on 12.10"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by buzzingrobot on 2013-02-07
Installing the Nvidia driver has failed here on a new 12.10 installation.

I installed from the DVD, ran the updates, rebooted, then selected the 310 series drivers from "Additional Drivers".  After a reboot, the logon screen was not the 1920x1200 screen I expected.  I'd guess it is 800x600, if not less.

After logging on, I was presented a screen with no dock and no panel.  I presume they were off the edge of the screen.

Via a console, I saw that the Nvidia install had not created an xorg.conf file.  So, I created that with "sudo nvidia-xconfig" and verified that it was correct.

Still, nothing changed after rebooting.  I've also booted in recovery mode and run through those drills with no change.

This is a machine that has previously run 12.04/12.10 with the Nvidia driver with no problems.

Short of reinstalling from scratch, how can I repair this?

---

### Post by jeremyswalker on 2013-02-07
If I remember correctly, you need to install "linux-headers-generic". Then, re-install the Nvidia driver. I had the same problem. For some reason the package is not installed automatically, like it should be.

---

