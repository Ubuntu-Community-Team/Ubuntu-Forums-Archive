---
title: "problem after the upgrade to 7.04"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by coldleg on 2007-04-30
after the upgrade i wanted to restart my computer, but instead of the log on screen came nothing, the screen turned black. i typed in my name and my password and heard the sound that comes usually, but the screen was still black. i think that my nvidia driver is the problem. is it possible to correct the problem???

---

### Post by coldleg on 2007-04-30
has nobody an idea?

---

### Post by bulldog on 2007-04-30
Boot into recovery mode,and type the command ```
sudo dpkg-reconfigure xserver-xorg
```

You should install the restricted modules,and the correct driver for your graphics.

---

