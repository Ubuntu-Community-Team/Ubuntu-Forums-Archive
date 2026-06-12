---
title: "Preventing a package from being upgraded"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by mwildam on 2010-08-10
I have manually installed the XVidCap from the sourceforge because the version in the Ubuntu repository has a major bug with recording sound.

Whenever updates come along, I get the XVidCap checked and have to manually uncheck. If I forget to uncheck, I get the buggy version back.

Is there a possibility to mark that package for manual update only or just hide it from the update proposals?

---

### Post by lechien73 on 2010-08-10
You can lock a package at a particular version through Synaptic. Go to **System > Administration > Synaptic Package Manager**, highlight the package you want to lock, select the **Package** menu and choose **Lock Version**.

Now you won't get prompted for upgrades to the locked package.

---

