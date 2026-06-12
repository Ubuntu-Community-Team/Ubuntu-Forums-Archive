---
title: "Nvidia + dual monitors = no vsync on primary display"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ChrT on 2009-09-03
As mentioned in the title, I'm running a dual screen setup, with an Nvidia Geforce 8800GTS 512 card. My two monitors are running at 1600*1200 and 1920*1200. I've got the 185 drivers installed, but the vsync problem was there before I installed it too. I've configured my monitors' resolution and alignment with nvidia-settings, and I've got sync to vblank enabled there, as well as in the compizconfig settings manager. Still, there is terrible screen tearing present on my primary monitor, easily visible for example when playing video or moving a window horizontally - but on the second monitor, vsync appears to be working fine. The vsync problems only occur on the primary monitor, regardless of which one the display is set to sync to. Both monitors are set to their native refresh rate of 60Hz.

P.S.: Looking at the individual display settings under nvidia-config, it appears my primary display (the larger one) is set to a refresh rate of 59.95 Hz. I'm unable to change this setting, as it's still listed as 60 Hz in both the X server display configuration tab, and in the xorg.conf. Could this be the source of the problem?

P.P.S.: This is on a fresh alpha 5 install.

---

### Post by OliW on 2009-09-03
Perhaps related but I too run a twinview setup and on boot, I have horrid tearing on my secondary display. I just turn it off and on again and it's fixed.

Pain in the face... but only a small one.

---

### Post by ChrT on 2009-09-03
> **OliW said:**
> Perhaps related but I too run a twinview setup and on boot, I have horrid tearing on my secondary display. I just turn it off and on again and it's fixed.

Pain in the face... but only a small one.

Just to be sure: You turn the monitor power off and back, and that fixes the visual artifacts?

---

### Post by OliW on 2009-09-03
> **ChrT said:**
> Just to be sure: You turn the monitor power off and back, and that fixes the visual artifacts?

For me it does.

---

### Post by ChrT on 2009-09-03
According to Launchpad, this is a big issue that affects pretty much everyone who uses some combination of either nvidia, compiz, or more than one monitor, and is several ubuntu releases old. Sounds like it deserves more attention than it's getting to me.

P.S.: For the record, disabling one of the monitors fixes the vsync on the other one.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/423940](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/423940)

---

