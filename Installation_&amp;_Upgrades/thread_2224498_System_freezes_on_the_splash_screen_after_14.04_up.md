---
title: "System freezes on the splash screen after 14.04 update"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by nathanpc on 2014-05-16
Today I decided to upgrade to 14.04, right after the system reboot I noticed that when the splash screen came up, all the loading dots below the logo were orange (instead of white, then change to orange after part of the startup process is done). After a while it was clear that the system was frozen, I tried to switch using Crtl+Alt+F(number), but nothing worked, it was completely frozen. I tried power cycling it, same problem again. Does anyone have any idea why this is happening and how to fix it? 

By the way, my computer is a System76 Bonobo Extreme. Here's a picture of the splash screen:

[img]http://i.imgur.com/Jffr675.jpg[/img]

---

### Post by nathanpc on 2014-05-16
I was able to get a command line and when I try to start the X server, look what I get at the bottom:

[img]http://i.imgur.com/x3nXPGV.jpg[/img]

So apparently it's a problem with the Nvidia drivers. Any ideas?

---

### Post by nathanpc on 2014-05-16
Upon further investigation I was able to trace it down to **libticalcs2-11** which was unable to update because of a unmet dependency, which made the whole upgrade process to stop, which made the system reboot with half of the new packages installed and the rest of the old ones, causing the driver issues. After removing the library and running a **-f install**, I was able to get it to work again.

---

