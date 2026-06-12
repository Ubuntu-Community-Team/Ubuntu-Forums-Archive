---
title: "No X after breezy -&gt; dapper upgrade"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by Xploit on 2006-10-13
Overall the upgrade was fairly successful.  I had ati drivers installed on my breezy build.  Now its saying "no screens found" "no drivers for fglrx found" and "no drivers found".

Although, my xorg config file still has all the information the ati drivers had put in there when I installed them.  As of now, i switched to the "vesa" drivers and I have x working.  So should I go ahead and re-install the ati drivers?

Also, why do I have the same kernel as my breezy install.  but when I hit ctrl-alt-f1 and right above where I login it says, Ubuntu 6.06, so i know the upgrade was successful.

Thanks

---

### Post by rugmonster on 2006-10-13
You do have a different kernel. The ATI (and Nvidia) drivers have a kernel module that interface with the binary driver. When you upgrade the kernel, you have to reinstall the driver so that module is recompiled for the new kernel.

So to answer you question, yes, reinstall the ATI driver.

---

### Post by Xploit on 2006-10-13
Thats why I posted, because I am pretty sure it didn't update the kernel.  Because uname still says 2.6.12.  Also, my ndiswrapper is still working.  If the kernel got upgraded then this module should have stopped working. Eather way I'll reinstall the ati drivers.

---

