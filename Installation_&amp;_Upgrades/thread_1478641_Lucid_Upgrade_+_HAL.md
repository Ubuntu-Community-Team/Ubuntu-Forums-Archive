---
title: "Lucid Upgrade + HAL"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by cmcginty on 2010-05-09
What is the state of HAL in Lucid. If it is depreciated, why is not uninstalled automatically, or at least reported as orphaned by 'deborphan'.

On my desktop upgrade, HAL was still being started up on init, but on my laptop, HAL was disable, yet still installed.

Why can't the installer/upgrade 1. work consistently, and 2. actually figure out how to handle these obvious upgrade tasks.  :mad:

---

### Post by kansasnoob on 2010-05-09
Basically hal no longer "runs" during startup because it's tasks have been handed off to either the kernel itself, upstart, or whatever. But it appears that hal still does still work with things like pmount.

So AFAIK hal is still viable, it's just unnecessary while loading the various modules needed by the Linux kernel. I expect to see it further deprecated.

---

### Post by cmcginty on 2010-05-10
I figured out why HAL was still starting on my desktop. The mirror I used for my upgrade was out of date, so I ended up getting a beta release.

---

