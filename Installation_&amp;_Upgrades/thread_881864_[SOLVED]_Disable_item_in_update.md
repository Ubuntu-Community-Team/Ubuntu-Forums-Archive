---
title: "[SOLVED] Disable item in update"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by AxiomShell on 2008-08-06
Hi everyone.

I've got a Samsung R20 running **Ubuntu 8.04**. These laptops are notoriously problematic regarding graphic drivers (*ATI Radeon Xpress*).

I've just got my X configuration right, problem is, everytime I upgrade xorg-server, I'm without a screen (pretty boring).

**Is there any way to disable the notification to update a certain package** (eg xorg-server) **without removing it from the system**?

[SIZE="3"]Thanks![/SIZE]

---

### Post by Partyboi2 on 2008-08-06
Try locking the package version in Synaptic. Open synaptic package manager (system>admin>synaptic package manager) and search for the package that you  want to lock and highlight it and select "Package" and then "lock version"

---

### Post by AxiomShell on 2008-08-07
Worked perfectly.

Many thanks.

---

