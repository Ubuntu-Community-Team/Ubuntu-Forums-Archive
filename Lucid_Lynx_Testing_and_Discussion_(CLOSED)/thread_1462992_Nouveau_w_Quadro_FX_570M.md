---
title: "Nouveau w/ Quadro FX 570M"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jeggen on 2010-04-26
I am using 10.04 w/ the latest updates with NVIDIA Quadro FX 570M graphics card on a HP 8510w.  When I use the Nouveau graphics driver I cannot enable desktop effects and have reduced performance.  Is the Nouveau intended to work with the Quadro chipsetsp in 10.04 release streams or do I need to use the Nvidia proprietary drivers?  (I had it working for a while while using the xorg-edgers PPA, but that isn't a long term solution and xorg-edgers isn't compatible with the current kernel in 10.04.)

---

### Post by renkinjutsu on 2010-04-26
Nouveau itself supports 2D, you'll also need the nouveau Gallium drivers for 3D

---

### Post by jeggen on 2010-04-26
Thanks!  I saw that "Gallium" is for "experts" so I better stick w/ proprietary Nvidia.  I am assuming that 3D support is needed for desktop effects.

---

