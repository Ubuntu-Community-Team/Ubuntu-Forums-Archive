---
title: "Broadcom STA takes a long time connecting to network after upgrade from 9.10 to 10.04"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by spearofsolomon on 2010-04-26
Title says most everything.  Before the upgrade, when I started ubuntu, I would connect to the wifi network in a matter of seconds.  Now when it starts the "connecting" status whirls and whirls for minutes, and then the authentication box pops up as if my password is incorrect.  I have to click connect several times, sometimes cancelling and waiting and then retrying, before it will finally connect.  When I do connect the speed is the same as it ever was, and I don't get dropped again until I reboot.

I have uninstalled and reinstalled the proprietary driver, upgraded the kernel and headers, deleted and recreated the wireless profile, and none of these have had an impact.  I just have to try several times to connect and it takes up to ten minutes.  I will try again and post a dmesg if there is any useful information there.  Right now I'm using a wired connection.

---

### Post by aysiu on 2010-04-26
I doubt this will get addressed before the release on Friday, but you should file a bug report on this problem.
[http://www.ubuntu.com/community/reportproblem](http://www.ubuntu.com/community/reportproblem)

---

### Post by spearofsolomon on 2010-04-26
Ok.  I will wait until after the release, upgrade all my packages, and if I'm still having the problem I'll file the bug.

Question if you have time: in the package manager I see that I have bcmwl-kernel-source installed, but I don't have the broadcom-sta-common package installed.  I used the "Hardware Drivers" to get my wifi working in 9.10 - what's the relationship with that broadcom-sta-common?

---

