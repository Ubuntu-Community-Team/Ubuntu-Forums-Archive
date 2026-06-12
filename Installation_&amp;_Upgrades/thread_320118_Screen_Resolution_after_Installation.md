---
title: "Screen Resolution after Installation"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by Origin on 2006-12-16
I installed Ubuntu 6.06 LTS on a Celeron 600 MHz via safe graphics mode. During the installation, I noticed certain things couldn't be displayed by the 640x480 resolution, but I thought it was just a temporary result of using safe graphics mode to install, so I pressed enter when I couldn't see whatever was down there (to go to the next step).

But now that it's installed, that's still the only resolution I can choose from System->Pref->Screen Resolution. I don't know what to do. I've looked around and I don't think anyone has experienced the same problem.

---

### Post by mlind on 2006-12-16
backup your /etc/X11/xorg.conf and then try to reconfigure xserver to add more resolutions
```

sudo dpkg-reconfigure xserver-xorg

```

If you have NVIDIA or ATI gfx card, consider installing proprietary drivers, those usually perform better and add support for newer piece of hardware.
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Origin on 2006-12-16
It's a bundled intel graphics chip, not ATI or nVidia

---

