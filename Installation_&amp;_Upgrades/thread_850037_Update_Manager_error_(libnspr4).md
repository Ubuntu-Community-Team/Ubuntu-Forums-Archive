---
title: "Update Manager error (libnspr4)"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by siloko on 2008-07-05
Hello,

I have a persistant error after the last routine update which prevents a package installing - the apt error is:

E: /var/cache/apt/archives/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.2_i386.deb: trying to overwrite `/usr/lib/libnspr4.so', which is also in package libnspr4

I have tried sudo dpkg --reconfigure -a but the same problem remains.

Does anyone have any suggestions?

Thanks

---

### Post by LinuxRocks713 on 2008-07-05
It's telling you that your current libnspr4 library is *conflicting* with the package you are trying to install.

Solution:

sudo apt-get remove libnspr4
sudo dpkg --install libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.2_i386.deb

---

### Post by siloko on 2008-07-05
That's done it - thanks

---

### Post by andoty_jazz on 2008-07-07
Yay! This solution helped. **@LinuxRocks713**, thanks much.

---

### Post by asac on 2008-07-11
> **LinuxRocks713 said:**
> It's telling you that your current libnspr4 library is *conflicting* with the package you are trying to install.

Solution:

sudo apt-get remove libnspr4
sudo dpkg --install libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.2_i386.deb

Hey, please dont post these instructions as we want to test the upgrade _without_ these. We have uploaded a fix and now people who run into this dont test our fir, but follow your procedure - which removes precious testers from us.

---

