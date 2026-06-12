---
title: "hg216D HDMI monitor resolution issue"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by adellalin on 2010-02-08
I just installed 9.10 on my hp pavillion a171On and monitor HG216D HDMI. the monitor displays up to up to 1680x1050 resolution but I only have 800x600 resolution available so display is all screwed up. How can I fix that.

Thanks!

---

### Post by dstew on 2010-02-09
Look in System --> Administration --> Hardware Drivers to see if there is a third-party driver available for your display hardware. If so, install it.

Otherwise, look in System --> Preferences --> Display. See if it will detect your display monitor. If it does, you can probably change the resolution to something better.

If these steps don't help, you might have a driver problem with your display adapter. If you think that is the case, in a terminal window, enter the command```
sudo lshw -C display
```Post the output to the forum.

---

