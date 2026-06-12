---
title: "Intel 4965 wireless"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by florus on 2008-11-02
The Intrepid release notes state that systems with an Intel 4965 wireless chip will lock up after upgrading and that an updated driver is required. Can I install the new driver before the upgrade as my laptop needs a wireless connection to access the driver?:confused:

---

### Post by florus on 2008-11-02
Has anyone successfully upgraded to Intrepid on a laptop with Intel 4965 wireless networking?

---

### Post by spongypants23 on 2008-11-02
> **florus said:**
> Has anyone successfully upgraded to Intrepid on a laptop with Intel 4965 wireless networking?

Yep. I installed the package "linux-backports-modules-intrepid" after upgrading. You could also try doing this before upgrading. I'm not sure if the package will be removed during the upgrade process though.

If it does remove the package, you can connect your laptop with a cable, download and install the package, and then it should work. 

This will keep your system from kernel panicking, hopefully. However, I'm still experiencing random stalling of the connection, and as far as I know, there is no fix for that yet.

(Note that I was able to run for a few minutes in 8.10 before the computer panicked. This may be the case for you as well, just be sure that no high-internet-usage programs run at startup.)

---

### Post by florus on 2008-11-02
Thanks for that. I think I will wait before I upgrade - Hardy works perfectly so I am in no hurry to change.

---

