---
title: "Can't report bugs on Lucid through Apport"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Thomar on 2010-03-08
I'm running the Alpha version of Lucid Lynx, and I've already come across three problems I can't report with Apport (one has to do with login, one has to do with Rhythmbox, and one has to do with Apport itself.)  In all three cases, Apport can't report them (in the case of Rhthymbox, it explicitly said it can't), and I can't post them on Lauchpad because the only link I can find redirects me to a wiki page which tells me to use Apport to report bugs.

How am I supposed to submit bugs to launchpad when the bug tools don't work?

---

### Post by Thomar on 2010-03-10
I'm gonna bump this one again...

How do I submit a launchpad bug through the website?  I can't submit certain bugs through apport.

---

### Post by Keyper7 on 2010-03-10
Did ubuntu-bug work?

---

### Post by teh603 on 2010-03-10
There's two greyed-out updates pending (udisks in particular) in the update manager that seem to be preventing Apport from working. At least in the AMD64 version.

---

### Post by dcstar on 2010-03-10
> **teh603 said:**
> There's two greyed-out updates pending (udisks in particular) in the update manager that seem to be preventing Apport from working. At least in the AMD64 version.

In Synaptic select only the udisks package for Upgrade, that will then remove the old libgparted packages and install the new one correctly.

The new version of gparted can then also be upgraded.

It seems the upgrade scripts for this package are not correct.

---

### Post by Thomar on 2010-03-11
> **Keyper7 said:**
> Did ubuntu-bug work?

Ah, that works.  Thank you!

---

