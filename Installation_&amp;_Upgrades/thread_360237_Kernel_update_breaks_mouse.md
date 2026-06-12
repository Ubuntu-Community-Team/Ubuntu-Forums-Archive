---
title: "Kernel update breaks mouse"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Frem on 2007-02-12
I'm using Ubuntu 6.06 due to hardware compatability issues with 6.10.

The recent kernel update (2.6.15-18-386) has broken my mouse. I'll be dragging a window, and if I move the mouse too quickly, the pointer will move faster then the window, and the window will stay where it is. Same with scrollbars. Also, I'm having to randomly click on buttons multiple times before they'll register. This is pretty insane. 

It happens on both my touchpad and my USB mouse. Does anyone have any ideas?

---

### Post by mr.v. on 2007-02-13
In case you haven't already tried, does booting with the older kernel version -27 still cause problems? If not, just stick with booting the -27 and remove the -28 revision and wait until -29 to see if whatever was messed up is resolved. If your kernel works fine and there isn't a critical security vulnerability or performance flaw in your current kernel...there is really no reason to update it anyway.

Hope this help...

---

