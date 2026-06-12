---
title: "Kernel Issues on upgrade"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by yanom on 2012-02-26
Every time update manager comes up, I get treated to this dialog box:
> 
**Not all updates can bet installed**
Run a partial upgrade, to install as many updates as possible

This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu

[Partial Upgrade]  [Close]

 in the upgrade window, the following packages are unselected:

linux-generic
linux-headers-generic
linux-image-generic

so it can't get the latest kernel. Why?

---

### Post by magowiz82 on 2012-03-13
same issue here with new 3.0.0.17 kernel

EDIT: mine issue is now solved, perhaps I updated package lists in the middle of a developer commit.

---

### Post by Frogs Hair on 2012-03-13
The kernel showed up in the update manager yesterday, but the boxes were unchecked . I waited until today because that means the update is incomplete. I ran check for updates today and the needed packages were found and I just finished installing 45 minutes ago.

Had I installed the packages yesterday via Synaptic it would have been a partial upgrade and those can be a problem . I especially would not use the option for a kernel. I would run check for updates in the update manager , reload synaptic, or run following before attempting the update.  ```
sudo apt-get update
```

---

