---
title: "Advice for upgrading to Karmic on MBP5,3 with refit"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by amd-64 on 2009-09-20
I am looking for advice on how to upgrade from Jaunty to Karmic on a MBP 5,3 or 5,5 that currently dual boots OS X and Jaunty with rEFIt.

Is it essential to use EFI boot, do I have to remove rEFIt. I understand that since 9.10 Alpha 5, grub2 is now by default. I will not upgrade right away, likely not until 9.10 beta is released. 

Thanks for all your help.

---

### Post by amd-64 on 2009-10-09
Okay. I upgraded the *macbookpro5,3* to Karmic. I did a fresh install on a new partition under refit. 

Everything works, sound needed the same workaround (recompile alsa from source alsa 1.0.21 works).  Wireless kept dropping and even freezing the entire system (thank you Broadcom), this was very annoying. I also recompiled the driver from source and it now works flawlessly. 

The heat problem is still there. The fans are stuck at 2000 rpm no matter what. If you change it manually to 3000rpm, the GPU temp goes from 70C to 52C, with a tolerable increase in noise. Alternatively, you may install the smcfancontrol script.

---

### Post by hanzomon4 on 2009-10-09
I don't use refit... even with jaunty. I Just hold down the option key

---

### Post by amd-64 on 2009-10-23
Didn't know you could do that. How do I remove refit.

---

