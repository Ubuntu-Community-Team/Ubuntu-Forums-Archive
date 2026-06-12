---
title: "No GUI after Install"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by Sloppy on 2005-04-28
Hi all!

I've just installed 4.10 but don't get the GUI when I boot into it.

I'm wondering if it's possible thats I didn't set it to VGA when asked at installed (left on default ... VERSA i think).

Anyone got any hints?

---

### Post by ape on 2005-04-29
Take a look in the /var/log directory for the Xorg.0.log file.  See if there are any errors in this log file to tell you what might be going on.

---

