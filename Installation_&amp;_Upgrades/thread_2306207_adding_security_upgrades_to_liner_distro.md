---
title: "adding security upgrades to liner distro"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by JaapS on 2015-12-13
Hello,

Got a little problem with an embedded ARM box containing a linaro distribution.
In sources.list only the "main" trusty port is there but that means I won't get any security updates, when adding deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) trusty-security main universe multiverse and re-running apt-get update/grade I now get a list with packages that needs an upgrade but I am afraid they will mess up  some linaro-specifick things.
I don't see kernel updates in it so on hardware level it should be fine but I do see a lot of org updates and the liner dist for this hardware has probably some hacked  closed drivers inside.
Is there a way to tell apt-get to update all expect packages provided by linaro inside /etc/apt/sources.list.d/?

---

### Post by ian-weisser on 2015-12-13
Hmmmm. Yes, but I cannot think of an easy way.
This kind of conflict is supposed to be handled by the archive/repository managers through distro Q/A and testing, not by individual users....

The problem is that apt assumes you trust entire sources, but you are adding two sources that may conflict.
Apt isn't clever enough to resolve that kind of conflict - by default, apt wants to upgrade to the higher-versioned package, regardless of source.
It's possible to list packages that apt shouldn't upgrade (it's an apt.conf setting) but that means you must know *all* the packages you want to refuse to upgrade.

---

### Post by JaapS on 2015-12-13
I was afraid of that, else the linaro guys would have added the repo themselves I think.
Another option would be making sure not to upgrade package x,y,z? (the kernel itself and the boot loader for starters, could dig trough the linaro's package list to decide which ones I want to keep for sure)

---

### Post by ian-weisser on 2015-12-13
See man apt_preferences for the complete guide on how to prioritize, pin, block, select, and otherwise fiddle with apt's logic.
It's rather advanced. It's very powerful. It does not have a safety net - it will do *exactly* what you tell it to do, regardless of consequences.
If you use it, backup your data.

---

### Post by JaapS on 2015-12-13
Thanks Ian!

---

