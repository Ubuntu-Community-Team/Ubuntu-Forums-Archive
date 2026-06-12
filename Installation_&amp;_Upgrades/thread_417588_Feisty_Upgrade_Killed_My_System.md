---
title: "Feisty Upgrade Killed My System"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by kevmartin on 2007-04-21
Yesterday I thought I would check into upgrading to 7.04 - so first downloaded the CD to run without making any changes, as a test run.  That went OK, seemed fine, cute desktop effects and stuff :-) I figured theres bound to be plenty of other more practical goodies too, lets go for it.

So I upgraded overnight, and now have a problem:

After the first boot I got a notification that my ATI card needed an unsupported driver or something, so I checked the box to enable it, and rebooted - no problem.  Then when I got around to trying the desktop effects got the message (composite extension not available) or similar.  A read on the forum seemed to suggest I'd be better off going back to the driver that had come with the Feisty distro instead of the one I had enabled.  So I disabled it, rebooted, now X can't start, I can only get a command line.

Any ideas?

Thanks in advance.

---

### Post by noxxle on 2007-04-21
sudo dpkg-reconfigure xserver-xorg

---

### Post by kevmartin on 2007-04-21
> **noxxle said:**
> sudo dpkg-reconfigure xserver-xorg

Thanks - I will give that a try when I get a chance to get out of windows and reboot :)

---

### Post by kevmartin on 2007-04-21
Thanks again - worked like a charm :)

---

