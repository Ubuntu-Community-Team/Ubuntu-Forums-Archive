---
title: "Easiest way to install a new monitor and video card"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by Geekkit on 2007-08-20
If I upgrade my hardware to use a different (new) monitor/LCD panel and a different (new) video card (same manufacturer - NVidia), then should I just boot into safe mode and simply type:

sudo dpkg-reconfigure xserver-org

And all should be fine?

---

### Post by jakev383 on 2007-08-20
That's what I would do.  It may require some additional configuring, but that would be my first step.

---

### Post by dabl on 2007-08-20
I would change my setup to a VESA display first, before replacing the hardware.
```

sudo dpkg-reconfigure xserver-xorg
``` and choose "NO" to autodetect, and then choose "VESA" as the display type.  Save this setup, then replace the hardware.  It should come up on the new hardware in GUI mode, and then you can proceed with installing the right driver. :)

---

### Post by Geekkit on 2007-08-20
Dabl, jakev383, thanks for your input/help. I'll try that. After 7.10 came out I noticed that I could (for the most part) be a brain-dead user and not have to worry about getting locked out of my OS.

:)

---

