---
title: "Ubuntu 21.04 installation on ASRock IND NUC 1165G7"
date: 2021-07-14
forum: Installation &amp; Upgrades
---

### Post by jfaberna on 2021-07-14
I'm trying to install Ubuntu 21.04 on an ASRock NUC 1165G7 which is based on an 11th gen Intel Core i7 mobile chipset with Iris GFX. I can select the boot USB and then I see the normal GRUB2 screen that show booting with or without safe GFX.  Neither one boot, and there is no output on the screen, but the CPU fan starts running fast. 

I've also tested with Kubuntu 21.04. Same results.

The only way I can get Ubuntu installed in to install 20.04, enable wifi, then update to the newest 5.11 kernel. That fixes the gfx and LAN chips, but everything else is still 20.04 and not 21.04.

Any ideas??

---

### Post by jfaberna on 2021-07-20
I found a solution for this, but I don't know why it worked.  Normally I keep my TV set to HDMI 2.0/HDR, but it would not work with the 21.04 installation screen past the boot choice.

I turned HDMI 2.0/HDR off and I could install.  The kernel 5.11 updates have solve some of my issues on this hardware. Still a few display problem when I put HDR/HDMI 2.0 back on, but it mostly works.

---

