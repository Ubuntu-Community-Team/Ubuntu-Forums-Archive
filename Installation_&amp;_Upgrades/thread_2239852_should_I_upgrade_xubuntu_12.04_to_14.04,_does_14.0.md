---
title: "should I upgrade xubuntu 12.04 to 14.04, does 14.04 support old hardware"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by gertwildeboer on 2014-08-16
I run xubuntu 12.04 on a HP-mini netbook, now I get the message from updatemanager to upgrade to 14.04. I tried 14.04 once and lost hardwaresupport for eg the onboard sd card reader, screen brightness control, does upgrading also installs new drivers and will I loose the same functionalities as with a normal install, or wil the upgrade use the drivers already installed in the 12.04 version?

---

### Post by ajgreeny on 2014-08-16
Much better to try the new 14.04.1 point version on a live USB and see if that works as a live system on the netbook.  If it does, do a clean install.

However, as you will now have install medium available you could try the update, and then if necessary, and the update fails, clean install over the failed update.

---

### Post by grahammechanical on 2014-08-16
Remember, the live session runs on an open source video driver. Your installed system may be using a proprietary video driver. My advice, if upgrading would be to de-activate the proprietary video driver and use the open source video driver for the upgrade.

Ubuntu 14.04 will use the drivers that come with the Linux kernel in 14.04 and not the drivers that came with the Linux kernel in 12.04. Hence, the value of running a live session before hand. One more point, have a look around the forum and notice the number of people reporting that they did the upgrade and now things are broken. This is why some of us recommend a fresh install.

Regards.

---

### Post by gertwildeboer on 2014-08-17
Thanks for your support, but I already did a fresh install and found that some hardware was no longer supported in the 14.04, that was the reason to downgrade to 12.04 in the first place.

So the question is if there's a difference beween a fresh install and performing the upgrade regarding the support of older hardware, does the 14.04 upgrade takes over the drivers from the 12.04 installation or does it uses the same set of drivers as with the fresh install, in that case it makes no difference and it would be better stick with the 12.04.

---

### Post by ajgreeny on 2014-08-17
You will have new drivers when you either upgrade or clean install, so you may have a hardware compatibility problem of some kind with the newest version of xorg which is in 14.04.

What is your graphics hardware?  That may give us more chance of helping you get to a working 14.04 install.

---

### Post by gertwildeboer on 2014-08-18
It's a HP mini netbook, it has a *intel atom d4xx/n4xx/n5xx integrated graphics controller, subsystem: hewlett packard company device 148a* (from sysinfo)
But the graphics is not the problem, when I fresh installed 14.04 some mobo functions were not supported like controlling the screen brightness and the sd card reader
I guess if 12.04 runs well on such a old and slow netbook it's better to stick with that version as long as it is supported (2017?)

---

