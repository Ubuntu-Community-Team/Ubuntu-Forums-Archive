---
title: "alternate cd upgrade needs internet connection????"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by daemmon on 2010-10-17
not having a working internet connection, i decided to upgrade from 10.04 to 10.10 by using the alternate cd. i followed the instructions on the ubuntu site, but, although i tell the installer not to use the internet, it tries to fetch packages from archive.ubuntu.com and it ends up with an error, reverting all changes (i have NO internet connection). i'm at my wit's end. please help!

---

### Post by aysiu on 2010-10-17
> **daemmon said:**
> not having a working internet connection, i decided to upgrade from 10.04 to 10.10 by using the alternate cd. i followed the instructions on the ubuntu site, but, although i tell the installer not to use the internet, it tries to fetch packages from archive.ubuntu.com and it ends up with an error, reverting all changes (i have NO internet connection). i'm at my wit's end. please help!
Go to System > Administration > Software Sources and uncheck all the sources that are **not** the Alternate CD. Then when asked to Reload, reload.

---

### Post by daemmon on 2010-10-17
when i do so, it gives an error saying 
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

p.s. i do actually have a wireless internet connection which, for some unknown reason, even though it used to work perfectly, now stops working after about 20-30sec and the only way to get it back working is to reboot - i've tried various solutions found on the web to make it work again, but to no avail. the only address that responds to ping is that of the router's, but i cannot even access the administration console - only ping works on it. on my wife's laptop running windows 7, it works just fine

---

### Post by aysiu on 2010-10-17
Hm. Could be this bug?
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/614993](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/614993)

---

