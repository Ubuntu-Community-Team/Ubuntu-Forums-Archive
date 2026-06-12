---
title: "Gutsy - Dual Monitors &amp; nVidia GeForce 8600 GT"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by puleen on 2007-10-19
It seems that gutsy doesn't auto-detect the card, nor the appropriate driver and on top of that it doesn't detect the dual monitors on the card either. Annoying!

---

### Post by erat123 on 2008-01-17
I agree!!!  This card should be more supported.  I mean, it works just fine, compiz runs.  But, you're right, it doesnt detect the dual head part.... i'm not impressed.  This card should be popular enough.  idk how to write drivers or i would.

---

### Post by peitschie on 2008-01-17
Gutsy doesn't autodetect the card quite true... it is relatively straightforward to install the latest nvidia drivers using Envy however: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Dual head setup is a little strange.  Ubuntu cannot do it automatically yet. Here is a tutorial to get you started though: [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

---

### Post by erat123 on 2008-01-17
i ended up going into bash and running

```
sudo nvidia-settings
```

that let me configure it w/o any trouble

---

### Post by peitschie on 2008-01-17
That'd also work ;).  I clean forgot about that been so long since I've configured my card :D

---

