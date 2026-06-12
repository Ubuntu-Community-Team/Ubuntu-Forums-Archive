---
title: "Ubuntu 14.10, Kernel Upgrade, unsuccessful boot"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by sean_kidder2 on 2015-05-01
I am running Ubuntu dual boot (Windows 7/Ubuntu) on a Lenovo Thinkpad, E550, Intel i7, 8GB RAM, all SSD disk.  Graphics is a hybrid - Intel HD graphics with an available AMD Radeon card.  I recently upgraded to 14.10 with no issues at that time.

Yesterday I allowed software update to upgrade my Linux kernel from 3.16.0-34 to 3.16.0-36.  However, after that installation, when I boot normally, I get the normal GRUB screen, but when I select Ubuntu, it goes to aa all purple screen and never proceeds from there.

From the GRUB menu, I can successfully boot when I pick the 3.16.0-34 version.  From Google searches and such, I started with assuming that the issues was graphics driver related, so I've been re installing and trying different graphic drivers, but no luck so far.

Any suggestions for how I can address this?  Could it be an issue other than graphic drivers?  One post I saw about Lenovo seemed to indicate a "low latency" build of the OS would help - but I want to be sure that makes sense before trying something that unique.

Thank you.

---

### Post by sean_kidder2 on 2015-05-01
I upgraded to 15.04 and the problem went away - but interestingly enough after the upgrade to 15.04 the default kernel on reboot is 3.16.0-34 - so I'll see what happens if it looks to do a kernel upgrade again.

---

### Post by Frogs Hair on 2015-05-02
When I did my 15.04 upgrade the kernel from the previous release was removed during clean up, so it might be driver related as you thought.

---

