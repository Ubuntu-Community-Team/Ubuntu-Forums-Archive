---
title: "Upgraded stuff and now x wont start"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by fsteveb on 2007-12-05
I tried to add packages to be able to compile X11 code. I think I added something I should not because the x server won't start. It gives me this litttle dos like window that says the x server tried to start 6 times and could not. I press OK and it tries again with the same screen. I added a bunch of packages to install and I was running on the upgraded nvidia driver. One of the things that I think may be causing a problem is I upgraded the g++ compiler to 3.4 from 3.3. I read in the forums the compiler needs to be the same as the kernal.  I am running the latelst 7.10 workstation download. My question is how do I restore the original working versions?
:confused:

---

### Post by Severun on 2007-12-05
Try re-installing your restricted modules.  If you have an nvidia or an ATI card it may be that the upgrade removed the drivers you were using.

Also if you are using an ATI video card, there have been problems reported on Gutsy with the fglrx driver, you may want to try a different driver for now, or disable some of the higher end features to get it to work.

---

### Post by fsteveb on 2007-12-05
It's a vaio laptop with a nvidia Go 7600 card.
It was working fine.
OK, how do I reinstall the driver when i can't get it to do anything beyond the OK error message?

---

