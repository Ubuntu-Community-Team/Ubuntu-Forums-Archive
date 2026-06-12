---
title: "Segmentation Fault on apt-get upgrade"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by AmateurDev on 2011-04-18
My computer sporadically gets segmentation faults multiple times daily, but when I try to upgrade, it consistently faults on the download. I've run```
sudo rm /var/cache/apt/*.bin
```but it still faults. I'm at a loss with this, is there something else I can do to solve the segmentation faulting?
Thanks!

---

### Post by Hedgehog1 on 2011-04-19
> **AmateurDev said:**
> My computer sporadically gets segmentation faults multiple times daily, but when I try to upgrade, it consistently faults on the download. I've run```
sudo rm /var/cache/apt/*.bin
```but it still faults. I'm at a loss with this, is there something else I can do to solve the segmentation faulting?
Thanks!

I hate segmentation faults... I really do...

The first thing to look at is the SMART status on you hard drive.  Using the Disk Utility, view the SMART status of the drive.  If you are having error on the drive, this is the most likely cause of them.

If the drive have no errors at all, then it gets much harder...


***The Hedge***

:KS

---

### Post by matt_symes on 2011-04-19
Hi

Can you post the exact output when it faults.

Does it happen with any other software or only apt ? I am a bit unclear on that. If it happens with other software check your memory and power supply as well as hard drive and check hardware in general.

If it only happens with apt then post back the full error messages.

Kind regards

---

### Post by AmateurDev on 2011-10-24
Sorry, for some reason I didn't get an email notification, so I'm not reading this until now. Unfortunately, I never solved the problem; the computer was transferred to a new case and installed with Windows 7(not my decision). I suspect that it was a hardware issue because it was plagued with seg faults all over the place, so this information might come in handy if it starts acting up again. Thank you for your responses!

---

