---
title: "How to disable kernel updates"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by notiones on 2006-08-23
Hi all,

I just finished repairing a laptop (gratis) because a kernel update broke it and so I want to disable kernel updates. It wouldn't be such an issue, but the client is 1000 miles away. That and I tend to customize a bit, which is probably why the kernel update broke it to begin with.

I am running Dapper.

Thanks,

Steve

---

### Post by baldy1324 on 2006-08-23
i know you can run ```
sudo aptitude hold kernel_package_name(whatever)
``` this holds the whatever package you type to hold its current version and not upgrade

---

### Post by Dr. Nick on 2006-08-23
The above should work, But you can also open synaptic package manager then search "linux-image" and you can lock the version that is currently installed

---

### Post by mlind on 2006-08-23
aptitude wants to upgrade anyway if pinning has been done using using synaptic, so I guess pinning using /etc/apt/preferences is better (or using aptitude hold?).
More about pinning see **man apt_preferences**.

Doesn't kernel upgrade always require dist-upgrade btw? Not sure if it's same for synaptic.

---

### Post by Dr. Nick on 2006-08-23
yes, pinning in synaptic only holds them back when apt is used, not aptitude

The kernel will update itself now from within the little built-in updater, If i recall correctly that used too not be the case, but it seems too be now. If the kernel did update remember the old version is still useable from the grub boot list in most cases

---

### Post by dgar on 2007-10-25
Confirmed that this is NOT the case in Gutsy.

"lock"ing a version of a package in Synaptic prevents the package from selection in update-manager.  :)

---

