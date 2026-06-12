---
title: "Any reason to upgrade Kernel on LTS?"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by impliedconsent2 on 2014-08-04
Now that 3.16 is out and has a goodly amount of improvements, is this a good reason to upgrade the kernel on LTS boxes?  I just don't know how Ubuntu handles new kernel feature-sets and bug fixes.

---

### Post by sammiev on 2014-08-04
If everything is working great and you are having no issues with the on board equipment why upgrade. If you add new equipment, you may need to. You can always take the update and if you have problems you can boot on advance mode and delete the new kernel. :)

---

### Post by impliedconsent2 on 2014-08-04
> **sammiev said:**
> If everything is working great and you are having no issues with the on board equipment why upgrade. If you add new equipment, you may need to. You can always take the update and if you have problems you can boot on advance mode and delete the new kernel. :)

I get that and have done it playing around with 13.04/13.10 - but now I just wanna do the LTS thing.  I guess my better question is - does Ubuntu take into account of these fixes to the kernel and eventually incorporate them?  Some drivers/fixes catch my eye *(Tegra HD-audio HDMI support, various support for Nvidia Tegra K1 and Kepler GPU, new audio drivers for misc. Cirrus, Realtek and Analog devices)* on nearly every subsequent release >3.12.  Just curious.

---

### Post by sammiev on 2014-08-04
> **impliedconsent2 said:**
> I get that and have done it playing around with 13.04/13.10 - but now I just wanna do the LTS thing.  I guess my better question is - does Ubuntu take into account of these fixes to the kernel and eventually incorporate them?  Some drivers/fixes catch my eye *(Tegra HD-audio HDMI support, various support for Nvidia Tegra K1 and Kepler GPU, new audio drivers for misc. Cirrus, Realtek and Analog devices)* on nearly every subsequent release >3.12.  Just curious.

They are careful with what they add to the LTS versions that have been release at an earlier date. You may have to take them manually unless they feel a need to force them out. Usually such updates like so you maybe better off to update to the next LTS version. 14.04 has been solid so far in my books.

---

### Post by kansasnoob on 2014-08-05
Two *must reads*:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

I prefer sticking with the original *stack* on production machines to avoid big problems but I also test the interim releases just so I know what's around the corner.

---

