---
title: "Errors during attempted install from LiveUSB"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jmmL on 2010-03-04
I managed to break something (finally!) by messing around too much with nouveau. I couldn't fix it and decided that a re-install from an alpha3 image on my usb stick would fix all my problems. After transferring my music onto another partition on the same hard drive, I then attempted to re-install.

I get a few error messages. One about there being "0 bytes left on this drive" and another that looks like this:> ubi-console-setup failed with exit code 4. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken. I think I also had one where the same process failed with exit code 1.

I'm the USB drive I'm using has 128MB set aside for persistent storage (I think), but has another 3GB or so of free space. Is there any way I can either remove the persistently stored data or expand the room for storage? I hope that this would get rid of the no-space error, which I suspect is causing ubiquity to fail.

---

### Post by jmmL on 2010-03-04
Solved issue by deleted .mozilla folder in the live-user's home folder (clearing the cache using firefox didn't seem to work). This bought me about 27MB of free space (on the USB drive), which was enough to complete the install with.

---

