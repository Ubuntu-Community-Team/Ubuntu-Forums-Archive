---
title: "Cannot boot into Windows 7 after install 10.04"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by RobGThai on 2010-05-05
To be specific, install from LiveCD.

I have Windows 7 installed and working on my laptop. I also have beta  version of Ubuntu 10 installed as well.

Then I boot into Ubuntu 10.04 from Live CD with option to try without  changing anything. There I choose to install Ubuntu on the laptop.
After that Windows menu was removed from the Dualboot menu, the only  "Windows-related" option present get me into the Windows screen with a  single command Window open with "X:". If I close this cmd window, my  laptop would reboot.

I'm completely new to all this, please help.

---

### Post by Mark Phelps on 2010-05-06
I'm guessing that you allowed the Ubuntu installer to shrink your Win7 partition to make room for Ubuntu.  If so, that was a bad idea because it risks corrupting your Win7 partition in the process.

Before you did this, did you use the Win7 Backup function to create a burn a Win7 Repair CD? IF not, why did you mess around with your partitions without having a way to repair any damage?

If so, boot from that CD and run Startup Repair three time.  That will restore Win7 boot but you will then have to reinstall GRUB for Ubuntu.

---

