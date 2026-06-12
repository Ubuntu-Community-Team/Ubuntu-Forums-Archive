---
title: "Black screen after upgrading from 14.04 to 14.10"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by rpaster1 on 2014-10-27
Please help. I did an upgrade from 14.04 to 14.10 two days ago from the software update/upgrade application. Everything appeared to work fine. After rebooting, I got to the login  screen and logged in, but instead of getting the graphical user interface, I got a black screen. After poking around on this forum, I tried to use a "control + Alt + F7" to get to a terminal session. This worked, but when i did a uname -a it showed I was still using generic 3.13.0.36, not 3.16.0.23. I signed out and have not been able to get to the graphical user interface. What do I need to do? Should I install 14.10 from scratch and not worry about the upgrade problem?

Any help would be greatly appreciated,

Bob

---

### Post by QIII on 2014-10-28
Hello!

Did you have any proprietary drivers -- in particular a graphics driver -- installed before you attempted the upgrade?

---

### Post by rpaster1 on 2014-10-28
Yes. I had the AMD Radeon HD 5700 driver I was using.

---

### Post by QIII on 2014-10-28
Did you install that from the repo or did you download it from AMD's website and install it?

When doing release upgrades rather than fresh installations, one of the most sure ways to turn the upgrade into a significant emotional event is to fail to uninstall the proprietary video driver.

You will likely need to completely uninstall the driver and reinstall it, but the method for uninstalling it depends on how you installed it to begin with.

---

### Post by rpaster1 on 2014-10-29
I'm not sure when you say "repo", but it was one of the "advanced drivers" (I think it's called) available through Ubuntu. I didn't go to AMD's website for it.  If I can get into a terminal mode, what would I do to remove the video driver ?

Thanks for your help,

---

### Post by rpaster1 on 2014-11-10
I finally decided to install 14.10 as a new install and that fixed things up. No proprietary display drivers will be used in the future.

---

