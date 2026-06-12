---
title: "System running slow after kernel update..."
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by megsona on 2007-09-30
I've been running Ubuntu on my Toshiba R100 (1GHz Centrino, 750MB RAM) laptop since Dapper, it's always been very responsive.

Yesterday I installed the kernel update and now things are running very slow. There was a problem after the first reboot, it got into an endless cycle of "ipw2100: eth1 : Failed to start the card", it looked like Launchpad bug #21344, however a hard reboot later and came back up no problem.

Now however, running Firefox with a few tabs open I can hear the cpu fan kick in and cpu utilisation hits 100%.

Is this affecting anyone else? Can I back out the change? Where can I see what changes were made to my system?

So many questions, thanks in advance!

---

### Post by Pumalite on 2007-09-30
Check first that you have previous kernel in Grub menu, then delete new kernel with Synaptic.

---

### Post by megsona on 2007-09-30
Thanks Pumalite, booting from the previous kernel from the GRUB menu stops the fault.

What will happen with the Gutsy upgrade though?

---

### Post by Pumalite on 2007-09-30
Don't do an upgrade. Save your data and do a clean install.

---

