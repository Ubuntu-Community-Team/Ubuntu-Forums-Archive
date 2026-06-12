---
title: "Dist Upgrade breaks system"
date: 2017-01-12
forum: Installation &amp; Upgrades
---

### Post by Superdude_123 on 2017-01-12
After running a apt-get dist-upgrade, my system has been hanging and needs to be hard rebooted. The system upgraded the following:

```
The following NEW packages will be installed:
  libsnapd-glib1 linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic linux-image-4.4.0-59-generic linux-image-extra-4.4.0-59-generic snap-confine
  snapd-login-service
The following packages will be upgraded:
  gnome-software gnome-software-common linux-generic linux-headers-generic linux-image-generic snapd ubuntu-core-launcher ubuntu-software

```
Any ideas what could be causing the problem?

Is there a way to undo those upgrades?

---

### Post by Impavidus on 2017-01-12
You can't simply undo an upgrade, but if the problem is the kernel upgrade (which is probably the case), you can boot an older kernel from the grub menu.

---

### Post by Superdude_123 on 2017-01-16
For future reference, removing the latest kernel solved my problem.

---

### Post by Impavidus on 2017-01-18
Don't forget to try new kernel updates later. Your problem may be fixed in a later version.

---

