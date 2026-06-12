---
title: "To upgrade or not?"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by max1e6 on 2010-11-18
Ubuntu 10.1

The update manager lists several "security" upgrades. In the past I have blindly followed the recommendations - with mixed results. On at least two occasions I have been locked out after applying the recommendations.

Recently, I have upgraded (using a fresh wubi install) to version 10.1. Shortly thereafter, I walked down the upgrade glory path and I had to reinstall because there were no previous kernels in my boot list.

I have seen posts where users have admonished upgraders: "you don't need to upgrade... it's stupid" But the upgrade manager warns of security holes.

What to do? Should I try the upgrades again. Is there a a way to protect myself from lock-out if things don't go well. I don't like "to follow the smoke."

---

### Post by bcbc on 2010-11-18
Upgrading and updating are two very different activities. Upgrading is about going from one release to the next. As long as the release you are on isn't at 'end of life', there is no security-based reason for upgrading.

Updating is different - security updates are there to address specific vulnerabilities. You can view the changes to assess whether or not the vulnerability applies to you, but in general it should be safe to apply the updates.

Wubi installs are vulnerable to grub updates - which also occurred in the 10.04 to 10.10 upgrade. Generally grub updates are not security updates. You can lock the version of grub-pc, grub-common and lupin-support in Synaptic and it won't prompt you to update them. Or just monitor the forums when you see grub updates and see if it is affecting other 10.10 users before running the updates yourself.

Lately all installs have been affected by partially updated kernels. When you only have one kernel e.g. 2.6.35-22 and you see an update for the same kernel, you are running a risk if the update fails, because you have nothing to fall back on. If you are concerned take a backup before updating or don't apply the update.

---

### Post by max1e6 on 2010-11-19
Thanks

> You can lock the version of grub-pc, grub-common and lupin-support in Synaptic and it won't prompt you to update them

Googled the how to on this. No luck yet. What's the way?

---

### Post by bcbc on 2010-11-19
> **max1e6 said:**
> Thanks



Googled the how to on this. No luck yet. What's the way?

Open synaptic, select package, click on menu:
 -->Package-->Lock Version

---

### Post by bcbc on 2010-11-19
I was just browsing around and noticed some threads saying that locking a package in synaptic doesn't prevent it from showing up in update-manager. I don't know if that is still a problem...

I'll check it out.

---

### Post by bcbc on 2010-11-19
> **bcbc said:**
> I was just browsing around and noticed some threads saying that locking a package in synaptic doesn't prevent it from showing up in update-manager. I don't know if that is still a problem...

I'll check it out.

OK - tested it and the old bug has been fixed: locking packages in synaptic removes them from the list offered by Update-manager.

---

### Post by max1e6 on 2010-11-19
Thanks again

---

