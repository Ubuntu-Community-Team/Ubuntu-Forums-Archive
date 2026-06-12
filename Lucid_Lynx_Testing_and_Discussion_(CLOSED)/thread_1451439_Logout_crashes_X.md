---
title: "Logout crashes X?"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by foobar66 on 2010-04-10
When logging out of the GNOME session, my system completely locks up.
Top half of screen is black. Bottom half shows white/black lines.
Only way out of this is to halt via power button.

I am not sure what is wrong. I checked the logout function immediately after a fresh install and then it worked OK.

Then removed a bunch of packages which I do not use and installed my custom built kernel.

After that logout no longer work.

I have little means to diagnose as system is completely locked when it happens.

Any other with this problem? Any suggestions to solve or diagnose?

---

### Post by mendieta on 2010-04-23
> **foobar66 said:**
> When logging out of the GNOME session, my system completely locks up.
Top half of screen is black. Bottom half shows white/black lines.
Only way out of this is to halt via power button.

I am not sure what is wrong. I checked the logout function immediately after a fresh install and then it worked OK.

Then removed a bunch of packages which I do not use and installed my custom built kernel.

After that logout no longer work.

I have little means to diagnose as system is completely locked when it happens.

Any other with this problem? Any suggestions to solve or diagnose?

Same here, lucid, open source ATI drivers, one user can login and out with no issues. The other one gets a black screen and a lockup. I'll let you know if I find a fix or a bug report.

---

### Post by mendieta on 2010-04-23
Here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/529882](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/529882)

---

