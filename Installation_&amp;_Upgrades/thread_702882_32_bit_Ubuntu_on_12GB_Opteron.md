---
title: "32 bit Ubuntu on 12GB Opteron?"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by kmand on 2008-02-20
We want to run a 32 bit Ubuntu kernel on a 12GB dual processor Opteron server (Sun V20Z). The box is going to serve remote desktops (Sunray)  and there are some driver issues that dictate a 32 bit kernel.

Is this possible and still make use of the 12GB (with 4GB limits per address space)?

We tried booting the standard desktop Gutsy 32 bit distribution disk, and the boot fails falling into an initramfs prompt. Do we need a different distribution disk?

---

Aside from the 32 bit issue, is a desktop or server distribution appropriate? It needs to serve full featured remote desktop , but  will mainly be a client for other services.

---

### Post by TuxImpersonator on 2008-02-23
Hey, 
A 32 bit system can only address 4 Gb of RAM in total, and wouldn't be able to use the rest. So you will need a 64 bit system to be able to use 12 Gb of RAM. Also you might want to try the server addition of ubuntu as it might suit your needs better.

Hope this helps

---

### Post by dstew on 2008-02-23
> the boot fails falling into an initramfs promptYou can try kernel parameters (like noapic nolapic acpi=off irqpoll) which you add to the kernel line. Press F6 at the first menu. Or, perhaps better, use the Alternate Install CD. It installs the same Ubuntu system as the Live CD, but uses a text based installer. Get it from the Ubuntu Download page, check the box below the Start Download button.

---

