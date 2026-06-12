---
title: "no fan, reboot instead of shut off"
date: 2008-07-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by excogitation on 2008-07-31
With the latest version of 2.6.26-4 sometimes my fan doesn't start spinning when turning power on and later does a heat related cold reboot.

Also shutdown or hibernate causes a reboot when the machine is supposed to turn off.

Furthermore with the 2.6.26-4 kernel series grub boot option vga=795 isn't working anymore.

Is any of these issues worth starting a bug report on launchpad?

---

### Post by CloudFX on 2008-07-31
Which alpha version of Intrepid are you trying to use?

---

### Post by psyke83 on 2008-08-01
> **excogitation said:**
> With the latest version of 2.6.26-4 sometimes my fan doesn't start spinning when turning power on and later does a heat related cold reboot.

Also shutdown or hibernate causes a reboot when the machine is supposed to turn off.

Furthermore with the 2.6.26-4 kernel series grub boot option vga=795 isn't working anymore.

Is any of these issues worth starting a bug report on launchpad?

Everyone is suffering from the shutdown and hibernate problems, it's a GDM bug/misconfiguration and will hopefully get fixed soon.

Your fan issue is suspicious, though. Kernel 2.6.26-5 is available, does it have the same problem? If you have a dual-boot system, do you have this problem in other operating systems?

> **CloudFX said:**
> Which alpha version of Intrepid are you trying to use? 

This question is only worth asking if the user is testing the Live CD, not an installed environment. Most users are upgrading on a daily basis (hopefully keeping in mind not to allow partial upgrades to break their systems), meaning that there is no concrete "milestone" for a running system.

---

### Post by excogitation on 2008-08-01
> **psyke83 said:**
> Everyone is suffering from the shutdown and hibernate problems, it's a GDM bug/misconfiguration and will hopefully get fixed soon.
I'm not talking about the logout issue.

> **psyke83 said:**
> 
Your fan issue is suspicious, though. Kernel 2.6.26-5 is available, does it have the same problem? If you have a dual-boot system, do you have this problem in other operating systems?
I will try the latest kernel and report back.
Fan works fine with earlier kernels, also with Win.

> **CloudFX said:**
> Which alpha version of Intrepid are you trying to use?
Alpha 3

---

