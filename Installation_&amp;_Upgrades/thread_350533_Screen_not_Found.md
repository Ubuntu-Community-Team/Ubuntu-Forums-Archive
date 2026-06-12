---
title: "Screen not Found"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by IgnacioMiller on 2007-01-31
Hey,

I'm trying to install Ubuntu 6.06 on my computer. I have an Nvidia graphics card. X wouldn't start off a fresh install. So then I downloaded the Nvidia binary drivers, and configured them according to the Wiki. However, I then got a 'screen not found' error. My identifier and devices are all lined up in xorg.conf. Any idea what's going wrong?

Thanks,
Ignacio

---

### Post by taurus on 2007-01-31
From a prompt, run

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by IgnacioMiller on 2007-01-31
Tried that, but I switched the Graphics card and it works now. Resolved.

---

