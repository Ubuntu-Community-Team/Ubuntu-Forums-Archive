---
title: "Blank screen after uprade to 12.04"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by nberger on 2012-04-28
Hello,

I had some problems with display after updating to 12.04 today. I managed to solve them, but since for once I couldn't find any information here beforehand I am posting the solution in case it helps others.

The problem occurred immediately after the GRUB screen, the display would go blank and the screen would say "no signal" or something similar. The boot process seemed to complete, but nothing was displayed. 

The solution was to reinstall the nvidia driver on the system, which was apparently broken by the update. The process is as follows:

1. Reboot
2. At the GRUB sceen, select "recovery mode" (2nd choice)
3. at the text menu, select "resume" (boot to graphical mode). This boots so some failsafe graphics mode (vesa?) which worked for me.
4. Install updates. At this point I rebooted, but nothing changed so I went back to recovery mode.
5. Select "Install additional drivers" (the "jockey" application) from the system menu
6. Select the recommended nvidia proprietary driver and click "Activate". The driver will be dowloaded and installed.
7. Reboot, and this time the normal boot should work.

Note that this was on a Kubuntu system, upgraded from 11.10 to 12.04, with an nvidia onboard graphics adapter. It may of course not work in other cases...

- Nicolas

---

### Post by kc1di on 2012-04-28
> **nberger said:**
> Hello,

I had some problems with display after updating to 12.04 today. I managed to solve them, but since for once I couldn't find any information here beforehand I am posting the solution in case it helps others.

The problem occurred immediately after the GRUB screen, the display would go blank and the screen would say "no signal" or something similar. The boot process seemed to complete, but nothing was displayed. 

The solution was to reinstall the nvidia driver on the system, which was apparently broken by the update. The process is as follows:

1. Reboot
2. At the GRUB sceen, select "recovery mode" (2nd choice)
3. at the text menu, select "resume" (boot to graphical mode). This boots so some failsafe graphics mode (vesa?) which worked for me.
4. Install updates. At this point I rebooted, but nothing changed so I went back to recovery mode.
5. Select "Install additional drivers" (the "jockey" application) from the system menu
6. Select the recommended nvidia proprietary driver and click "Activate". The driver will be dowloaded and installed.
7. Reboot, and this time the normal boot should work.

Note that this was on a Kubuntu system, upgraded from 11.10 to 12.04, with an nvidia onboard graphics adapter. It may of course not work in other cases...

- Nicolas
Note: It will not work with ubuntu 12.04 at the moment as the Nivida drivers cause compiz to crash

---

