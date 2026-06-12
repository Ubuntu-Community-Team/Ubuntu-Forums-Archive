---
title: "Problem with graphics on Lenovo G560 with Intel P6100"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by chetkgp on 2010-10-19
Hi All,

I am trying to install Ubuntu 10.10 on an Lenovo G560 laptop with Intel P6100.
Everything seems to work fine except for the graphics. The screen goes blank
when I enter startx from the console.

lspci shows the following for the graphics card :
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

In xorg.conf, I've tried drivers 'vesa' which gave me low resolution, and also 'intel' which 
blanked the screen again.

How do I configure this graphics card ?
Has anyone else faced similar issues when installing Ubuntu on this graphics card?

Any help with this would be greatly appreciated.

---

### Post by barinov2000 on 2010-10-21
same here. 10.04.1 AND 10.10...

---

### Post by mangwills on 2010-10-22
I encountered a similar problem with an eMachines laptop with P6000.

I followed instruction in [http://www.khattam.info/howto-install-latest-intel-drm-kernel-to-avoid-crashes-on-boards-with-intel-hd-graphics-2010-08-14.html](http://www.khattam.info/howto-install-latest-intel-drm-kernel-to-avoid-crashes-on-boards-with-intel-hd-graphics-2010-08-14.html) and it worked so far for me.

---

