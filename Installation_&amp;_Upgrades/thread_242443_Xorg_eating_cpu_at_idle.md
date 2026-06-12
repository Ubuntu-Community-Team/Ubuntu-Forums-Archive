---
title: "Xorg eating cpu at idle"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by Selidor on 2006-08-23
Hey.  After I did an upgrade last night on 6.06, I noticed my touchpad and keyboard are sluggish, occassionally freezing for a brief moment.  A top reveals that Xorg is using around 20-35% of the cpu at idle now.  I have upgraded xserver-core to 10.4, still same problem.  I downgraded to 10.0, still same problem.  It was fine until I decided to run the update notifier last night.  This happens under 2.6.15-23, and 2.6.15-26 kernels.  It also happens under my custom vanilla kernel 2.6.17.

My system is an Acer Aspire 5003 WLMi.  Sis 760 graphics.  AMD 1.8 Turion-64.

Thanks,
Scott F.

---

### Post by Selidor on 2006-08-23
Ok, nevermind.  After pulling my hair I finally found the problem.  It was ifplugd causing the cpu usage.  Donno why it but it seemed to start after the latest batch of updates I did last night.  Ifplugd was not acting up previously.  Anyway, there was no indication in top that it was hogging some cpu.  Xorg was at the top of the list.  Anyway, disregard this please.

Scott F.

---

