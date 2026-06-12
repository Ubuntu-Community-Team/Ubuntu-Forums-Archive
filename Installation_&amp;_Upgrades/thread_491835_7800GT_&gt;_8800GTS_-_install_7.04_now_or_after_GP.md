---
title: "7800GT &gt; 8800GTS - install 7.04 now or after GPU upgrade?"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by njparton on 2007-07-04
I'm currently running a system with a 7800GT graphics card that will be replaced with an 8800GTS tommorrow.

Given the problems with installing 7.04 on a system with an 8800 card, am I best to install 7.04 now, upgrade to the latest nvidia graphics drivers and then just replace my graphics card tommorrow?

Will Ububntu fall over with a change of hardware or will everything be OK? 

Looking at the various other 8800 related posts on this forum, I'm not sure whether I should wait until the 7.10 Ubuntu release if I wait to install after changing my graphics card?

Advice welcome!

Thanks

---

### Post by Analord on 2007-07-04
Advice is, edit your xorg.conf and change driver from nvidia to vesa
Uninstall your prop. driver.
Put your card in
Install driver again, enjoy.

---

### Post by njparton on 2007-07-04
> **Analord said:**
> Advice is, edit your xorg.conf and change driver from nvidia to vesa
Uninstall your prop. driver.
Put your card in
Install driver again, enjoy.

Thanks for that. What's the best way to uninstall the nvidia driver?

---

### Post by Analord on 2007-07-05
Well it depends which way you have installed it.

If you used the Restriced manager, use it to uninstall it.
If u used .run from NVIDIA site, i recommend doing the folowing.

sudo nvidia-installer --uninstall

---

