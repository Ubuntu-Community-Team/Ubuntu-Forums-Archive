---
title: "Compositing in Breezy- How to Disable?"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by Iandefor on 2005-10-16
I just upgraded my Hoary installation to Breezy. It went smoothly, except that
when I rebooted, I found that compositing was enabled. Since I run legacy hardware, I would prefer to run Breezy without compositing enabled. I had assumed it was the X compositing Manager, so I opened a terminal, typed in ```
killall xcompmgr
``` Although it seems that xcompmgr is not running (When I attempt to kill xcompmgr, it returns ```
xcompmgr: no process killed
```
Does anyone have any ideas? If this helps at all, I upgraded by updating my /etc/apt/sources.list file to the breezy repositories, and then typed in "apt-get dist-upgrade". Thank you!

**EDIT: I feel like an idiot now... I simply disabled compositing in etc/X11/xorg.conf and all is right with the world. However, if someone could please provide some ideas as to what actually happened, I'd appreciate it! **

---

