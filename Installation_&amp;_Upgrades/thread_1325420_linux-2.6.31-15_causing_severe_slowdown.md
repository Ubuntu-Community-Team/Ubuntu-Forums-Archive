---
title: "linux-2.6.31-15 causing severe slowdown"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by superbiskit on 2009-11-13
Thursday, I found "linux-image-2.6.31-15.50" from Karmic Proposed on the updates list.  I installed it successfully and rebooted.

The rebooted system immediately began exhibiting extreme slowness.  Logging into Gnome had not succeeded after 15 minutes (when I gave up).
Today, I booted into "Recovery Mode" and ran Aptitude.  The download phase went pretty smoothly, but it was 3 HOURS! later when the first "(Reading Database...)" pass had only reached 80% complete -- and I gave up on that.

I booted into linux-image-2.6.31-14, and all was well.

---

### Post by coffeecat on 2009-11-13
> **superbiskit said:**
> Thursday, I found "linux-image-2.6.31-15.50" from Karmic Proposed on the updates list.

<snip>

I booted into linux-image-2.6.31-14, and all was well.

Have a look at this:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.Use the -14 kernel. The -15 one is probably broken and no doubt will be replaced.

---

