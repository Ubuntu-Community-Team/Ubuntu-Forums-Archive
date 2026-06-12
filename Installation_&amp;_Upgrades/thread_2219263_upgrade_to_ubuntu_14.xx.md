---
title: "upgrade to ubuntu 14.xx"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by macstl on 2014-04-23
I have some cli instructions for upgrading to 14.xx from 13.  Can I upgrade from 12.04 tor 14.04 with no problem bypassing 13.10? Would it be better just to use the gui updater?

---

### Post by ian-weisser on 2014-04-23
> **macstl said:**
> I have some cli instructions for upgrading to 14.xx from 13
Hey, that's wonderful.
Of course, the *version* of 13.xx to 14.xx is important.
Release-upgrades from 12.04 or 13.10 to 14.04 have been tested and are supported.
Release-upgrades from 12.10 or 13.04 to 14.04 have not been tested and are not supported.

Your cli instructions shouldn't consist of much more than two steps:
1) backup your data
2) command: do-release-upgrade

> **macstl said:**
> Would it be better just to use the gui updater?
The gui updater is neither better nor worse than the command-line updater. They use the same engine.

---

