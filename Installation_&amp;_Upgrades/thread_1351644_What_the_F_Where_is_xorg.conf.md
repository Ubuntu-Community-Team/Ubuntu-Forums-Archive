---
title: "What the F? Where is xorg.conf"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by thirdmusketeer on 2009-12-10
I upgraded from 9.04 to 9.10 today everything went smoothly but when I booted, it gave me the message that 

Failed to load module "ati" (Module not found 0) error.

I embarked on a quest to figure out the problem, installed and un-installed 
xserver-org-video-ati 
tried to reconfigure using
dpkg-reconfigure -phigh xserver-xorg

but to no avail. Then out of nowhere I just deleted my xorg.conf and rebooted and voila everything works, I am not being ungrateful but I want to understand what has changed, I now don't have any /etc/X11/xorg.conf yet everything is working.

I am using the community ati package for my HD 2400 Pro card. As I understand fglrx will not work with this card.


Thanks in advance.

---

### Post by squaregoldfish on 2009-12-11
The newer version of X11 will work without an xorg.conf file, or at least try to - it has its own set of internal defaults to fall back on, and interrogates the hardware to get as close as it can to a decent set-up.

The chances are that you're running without specific ATI drivers, and therefore maybe missing some things - for example, it wouldn't surprise me if hardware acceleration isn't working. Check /var/log/Xorg.0.log to see what drivers it has or hasn't loaded.

I don't know anything about ATI cards to help you get the drivers reinstalled, but that's why X will work without an xorg.conf file.

Steve.

---

### Post by mikewhatever on 2009-12-11
As a matter of fact, Jaunty doesn't use xorg.conf either, so not sure why the surprise.

---

### Post by squaregoldfish on 2009-12-11
I'm on an upgrade path from Gutsy (might be time for a reinstall?!), so I've always had an xorg.conf file.

If you install the driver package for your card, will an appropriate xorg.conf file be created, or will X automatically pick up and use the correct drivers?

Steve.

---

### Post by mikewhatever on 2009-12-11
Don't know, it will probably leave it as is, cause it doesn't need creating it.

---

### Post by thirdmusketeer on 2009-12-11
> **mikewhatever said:**
> As a matter of fact, Jaunty doesn't use xorg.conf either, so not sure why the surprise.

Interesting, when I was running 8.10 I had proprietary drivers in the xorg.conf but by 9.04 the support for my card was dropped, but even in that case my installation needed the xorg.conf as it wouldn't boot properly without it. I wasn't aware of the fact that xorg.conf wasn't needed for 9.04 either.

Anyway I got my explanation. 

Thanks

---

