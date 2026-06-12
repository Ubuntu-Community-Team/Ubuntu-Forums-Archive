---
title: "Can't remove GRUB, reinstall 9.10 from LIVE CD"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by StarscreamD on 2010-08-17
I had Kubuntu 9.04 and Windows XP on a Dual Boot.

I upgraded using the update manager to 9.10. (I know, I'm a fool.) The Kubuntu install stated freezing hard on startup, just after the GRUB OS selection screen, at a blinking cursor and otherwise blank screen.

I'm pretty sure 9.10 will work great from a fresh install, but the live cd freezes after main Kubuntu boot screen and even Windows live cd only shows Windows partition. fixmb, fixboot, bootcfg etc. do NOT replace the grub as desired.

---

### Post by mitsios on 2010-08-17
If you can boot from a linux livecd, try this to remove grub:

```
dd if=/dev/null of=/dev/sdX bs=446  count=1
```Replace sdX with your drive

---

