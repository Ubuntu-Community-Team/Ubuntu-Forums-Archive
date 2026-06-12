---
title: "how to get security update when i upgrade to the latest kernel compiled on my own"
date: 2013-12-16
forum: Installation &amp; Upgrades
---

### Post by pramitkumarpal on 2013-12-16
I was into ubuntu 12.04 3.5.0-23 and i compiled a custom kernel and went to 3.12.5 .
After upgrading the kernel how to get the security updates?

ubuntu 12.04 LTS updates show in my update manager, but that should be invalid, shouldn't it? as i upgraded the kernel myself..

---

### Post by Frogs Hair on 2013-12-16
Kernel updates are based on the desktop meta packages and you will receive updates for the kernel 12.04 is supposed to be using and not the one you manually compiled. The update system doesn't detect the manually upgraded kernel and provide security updates for it. Please wait for a response from users that have an upgraded kernel installed. There is a way to keep the kernel from regressing when updates come, but I am not familiar with it.

---

### Post by Doug S on 2013-12-16
I often run with non-standard kernels. For updates, I boot with the normal kernel and do the update. Afterwards, I boot again with whatever kernel I need.

---

### Post by buzzingrobot on 2013-12-16
When you build your own kernel, you get to add the patches, too. :)

---

### Post by tgalati4 on 2013-12-16
You have a few options:

As Doug_S suggested, boot into the mainline kernel and do the updates--this is handy to have as a backup anyway.  Then once a year or every 6 months, recompile the kernel with your configuration and any patches that you have added.  When you update the source code (which sometimes lags the binaries as far as patches go) you will eventually get the patches in the mainline kernel source tree.  The other option is to evaluate the patches (by reading the changlogs) and not doing any updates at all until you find an update that patches a severe vulnerability--or fixes a problem with your hardware.

The pain (and time) it takes to compile the kernel has to be weighed by any benefits of kernel updates.  Because LTS kernels will receive updates (mainly security updates) for 5 years, you will want to review the changlogs to see what vulnerabilities got fixed.  If your system is not facing the internet or running a server, then you can probably do your updates once a year.

---

### Post by pramitkumarpal on 2013-12-18
Everyone thanks for the replies.:D :P

---

