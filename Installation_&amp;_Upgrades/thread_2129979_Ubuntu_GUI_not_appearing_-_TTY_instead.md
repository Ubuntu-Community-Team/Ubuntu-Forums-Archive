---
title: "Ubuntu GUI not appearing - TTY instead"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by BLaZuRE on 2013-03-27
I'm not sure how this happened, but my system was working fine (for months).  Maybe an update.

When I boot, I get the Ubuntu load screen with the scrolling circles.  After two rounds, I'm taken to the TTY1 instead of a login screen.  For some reason in the logs, XWindows errors out, saying it cannot detect any displays.  I've tried installing Ubuntu fresh on a different partition, but that doesn't work either.  I'm thinking it might be Grub2.

I am trying to install 12.04 LTS.  

I am using an ASUS VH238H as a monitor if that helps.

My grub line includes: ro quiet splash $vt_handoff

Thanks!

---

### Post by JRV on 2013-03-28
Try adding "nomodeset" to the options.

---

