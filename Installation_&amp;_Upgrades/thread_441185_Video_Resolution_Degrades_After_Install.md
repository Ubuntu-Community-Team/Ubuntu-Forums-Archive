---
title: "Video Resolution Degrades After Install"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Bill Bickley on 2007-05-12
My Feisty 7.07 CD uses 1280x1024 and 75 MHz as a live CD and during the install process, but once installed, I can't get above 1024x768 and 60 MHz.

Thoughts and suggestions?

TIA.

Bill

---

### Post by kyphi on 2007-05-12
In a terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

on the resultant screen use your up/down keys to scroll to the resolution you want and press the space bar.
Then enter and exit.

Sometimes it is sufficient to log out by pressing Ctrl+Alt+Backspace and then logging back in.  If that does not get the desired result just reboot.

Good luck.

---

