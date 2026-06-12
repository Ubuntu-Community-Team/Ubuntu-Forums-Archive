---
title: "Kernel updates remove Windows from GRUB"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by dnstalford on 2007-06-19
How do I stop this from happening everytime I update Ubuntu?  I install an update, reboot, and Windows has vanished from GRUB.  I'm not that familiar with linux yet and it takes me a little while to fix everytime it happens.

Is there a way to save me from doing this all the time?

---

### Post by merlinus on 2007-06-19
Make sure that your windows stanza in /boot/grub/menu.lst is below:

### END DEBIAN AUTOMAGIC KERNELS LIST

Otherwise it will be deleted every time there is a kernel upgrade.

You can still set grub to boot windows by default, if need be.

-merlin

---

