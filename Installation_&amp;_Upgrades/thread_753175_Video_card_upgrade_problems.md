---
title: "Video card upgrade problems"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by man_bash on 2008-04-12
Hi, I just bought a new nVidia 8800 GT graphics card, and Gutsy refused to boot. The monitor just goes off right after GRUB, stays off for about 2 minutes, then turns back on, but is stuck at "loading /etc/rc.local". Same thing happens when I tried reinstalling Gutsy and Feisty (both AMD64) by booting from LiveCD. The old video card is Voodoo 5500 PCI, and that worked fine. Any ideas? Thanks in advance

System specs:
MoBo  - DFI Infinity nf4x
CPU    - AMD Turion 64 ML-28
RAM   - 2 GB DDR400
Video card - XFX 8800 GT 512 MB
HDD   - 320 GB SATA WD + 250 GB PATA Maxtor

---

### Post by Partyboi2 on 2008-04-12
Following post number #4 from [here]("http://ubuntuforums.org/showthread.php?t=689436")

---

### Post by man_bash on 2008-04-20
First off, as I have tested, the video card itself was faulty. So I got a replacement 8800GT, some problems are gone (I can install and run Ubuntu), but there is still no proper driver. So far I have tried: 173.08 beta driver, 171.06 beta driver, 169.12 driver, all to no avail - with any of the proprietary drivers tried loaded Ubuntu starts and prompts me to either start in low graphics mode, or to configure card myself. It starts fine in low graphics mode, but when I try to configure the card myself (I would select nvidia as the video card driver, and choose 1600x1200 monitor), same thing happens and Ubuntu starts in low-graphics mode. When I tried to reboot in restore mode and chose "fix Xserver" (this is now Hardy) I can get high resolution, but still no 3D support, I cannot even enable any visual effects. Any ideas?

---

### Post by man_bash on 2008-04-20
> **Partyboi2 said:**
> Following post number #4 from [here]("http://ubuntuforums.org/showthread.php?t=689436")

tried all the step suggested, save for install of the packages - had to use Synaptic as my wireless card will not work in shell, and used newer drivers (see above) - no results whatsoever.

---

### Post by man_bash on 2008-04-20
Does anyone know how to get the 8800 GT work in 3D with Ubuntu? Should I ask in Multimedia and Video section instead?

---

