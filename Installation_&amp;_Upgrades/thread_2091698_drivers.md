---
title: "drivers ?"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by Culso on 2012-12-05
does anyone know where i could find drivers for a asrock z77 extreme 4 ?

---

### Post by jerome1232 on 2012-12-05
Everything should be built into the kernel, so no additional drivers should be required. Are you experiencing problems with any of the on board chipsets like the audio, video, or network?

---

### Post by Culso on 2012-12-05
nah, im just checking before making the move to ubuntu for good

---

### Post by mastablasta on 2012-12-06
> **Culso said:**
> nah, im just checking before making the move to ubuntu for good
 
 
drivers in Ubuntu are as mentioned part of kernel. this is different than in windows where they are mostly separate from kernel.
 
if after tests and install something is not working (as mentioned some specific chip like audio) you troubleshoot only that and it is possible (sometimes) to find separate drivers for it and then include them in kernel. however if it all works as it should then you are good to go.
 
edit: it is also worth mentioning that kernel gets regular updates, so drivers are often updated as well. that's the good side. the bad side is that after kernel update things can break... i had sound working well but after about a month an update came that broke it again.

---

### Post by Culso on 2012-12-06
what about my gpu ? (hd7850 2gb)

---

### Post by Mark Phelps on 2012-12-06
> **Culso said:**
> what about my gpu ? (hd7850 2gb)

Open-source Radeon drivers will be installed automatically -- even though System Info will not show that.

If you want restricted drivers, you will be presented that option -- but there are problems with those drivers in 12.10 and I would avoid installing them unless absolutely necessary.

---

### Post by grahammechanical on 2012-12-06
> here are problems with those drivers in 12.10 and I would avoid installing them unless absolutely necessary.

So, do not tick Install third party software during the installation process. Otherwise you will get the proprietary driver installed.

You can install the restricted extras package afterwards. It is in the Software centre. With 12.10 we go to System Settings>Software Sources and use the Additional Drivers tab if we want to install the proprietary driver after after installation.

Regards.

---

