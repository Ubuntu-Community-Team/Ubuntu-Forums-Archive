---
title: "Nvidia upgrade. Need to shut down x server"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by TylerHa85 on 2011-09-26
I just upgraded my graphics card to a Nvidia Geforce GT 430. I have downloaded the correct driver from nvidia. Now i'm trying to shut down X server but when i use this script:

sudo /etc/init.d/gdm stop

I receive an error message:

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm

Any suggestions about what to do next?

---

