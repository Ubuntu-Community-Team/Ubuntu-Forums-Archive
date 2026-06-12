---
title: "Kernel Bogey..?"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by John E on 2007-02-11
It's only during the past 2 or 3 weeks that I've become aware of the fact that Linux hardware drivers are often compiled into the kernel. Doesn't this have a knock-on effect for kernel upgrades?

For example, during the past couple of days, every time I boot intu Ubuntu, a pop-up balloon informs me that there are new upgrades available. 2 of them are kernel upgrades. Suppose I accept those upgrades and install them. Will I lose all the kernel-mode drivers that I've painstakingly installed - or is a kernel upgrade sensible enough to take account of this...? :confused:

---

### Post by m0e on 2007-02-11
I just got done spending an hour fixing my video drivers after doing the kernel upgrade, so no it isn't sensible enough to avoid this. And if you search the forums you can see how it can affect other kernel modules too, although the proprietary ATI driver I use seems to be my only victim this time. I usually wait a week or so before doing kernel upgrades but I knew I would have a couple of hours this weekend to fix any problems the upgrade caused. You can go into Synaptic and lock your kernel to a specific version number and I believe you will no longer be prompted to upgrade it, but I haven't done that so I am not sure how that works.

---

### Post by John E on 2007-02-11
I'd really like to know how to do that locking business. I went through an absolute nightmare installing certain drivers and I don't want to go through it all again...!

---

### Post by John E on 2007-02-12
Does anyone here know how to make Synaptic "lock the kernel revision" ? I found an option saying "favour the local installation" but I think that applies to all apps, not just kernel modules.

Alternatively, if someone is needing to upgrade a driver manually, is it safer to opt for a user-mode driver, rather than a kernel-mode one? Would that be a way to circumvent the problem I described?

---

