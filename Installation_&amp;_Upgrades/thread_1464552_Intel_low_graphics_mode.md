---
title: "Intel low graphics mode"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by Cobalto on 2010-04-28
Please help me defend our good name!

I have a weird problem on 10.04 RC and 9.10. On a freshly installed laptop I get this on startup:

[B]Ubuntu is running in low-graphics mode.

Following errors were found:

(EE) intel(0):[drm]Failed to open DRM device for
pci:0000:00:02.0: No such file or directory
(EE) intel(0): Failed to become DRM master.
(EE) intel(0): No valid FB address in PCI config space
(EE) Screen(s) found, but none have a usable configuration[/B]

I also get other error messages before and after the splash screen, but they only flash for less than a second and can't tell what they're saying.

Two other symptoms: I can't make an external monitor work, and I can't get Compiz to work.

The machine is a Sony Vaio VGN-C270FN. It belongs to a friend who wants to try Linux and isn't very impressed so far. Help, please!

lspci | grep VGA reports:
00:02.2 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Conroller (rev 03)

---

### Post by Cobalto on 2010-04-29
Anybody? Pleeeeaaaase?

---

