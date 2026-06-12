---
title: "VisualEffects will not Enable"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by GriGGerZ on 2010-04-22
Hi All

I have had the same problem in the Lucid Beta 2 and RC release. I can enable the nvida proptietary drivers but after the requested restart the machine flashes up a box with errors relating to nvdia, one of which is "NVIDIA(0) failed to initialize the NVIDIA Kernal module!... ect ect 

This places Ubuntu into a low graphics mode. 

I have enable and disabled both version 173 and the (current) recommended driver and still have the same problem. If I remove both drivers then Ubuntu boots into a higher res. If I then try to up the visual effects the box loads up the nvidia drivers, requests a restart after which I'm back to Low Graphics mode.

My machine is a Packard Bell (Brand new especially for Lucid release) :-)
Model ixtreme X5620 UK
Intel Quad Core Q8300
DDR2 4096 800MHz
Chipset Nvidia GeForce 7100

Has anyone else experienced this problem in Lucid?

GriGGerS

---

### Post by cariboo on 2010-04-22
Have you tried running:

```
sudo nvidia-xconfig
```

in a terminal and rebooted?

---

