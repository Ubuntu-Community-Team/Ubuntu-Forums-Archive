---
title: "ubuntu kernel comes up twice in startup screen"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by raspberryh on 2006-08-30
Hi,
I installed Ubuntu on a partition of my harddrive, w/ Windows XP on the other one. On the startup screen (from Ubuntu's bootloader), where I can pick Ubuntu or Windows, for some reason, Ubuntu kernel and the other option (I think it's Ubuntu kernel recovery mode or something similar) - they both show up twice. I have no idea why. Is there a way to fix this?
Thanks,
Heather

---

### Post by mlind on 2006-08-30
That's probably another kernel (a upgrade). You can remove it if you feel that newer kernel is working out fine. 

See System > Administration > Synaptic Package Manager. Search for linux-image

---

### Post by raspberryh on 2006-09-07
> **mlind said:**
> That's probably another kernel (a upgrade). You can remove it if you feel that newer kernel is working out fine. 

See System > Administration > Synaptic Package Manager. Search for linux-image

I did this, and it worked. Thanks so much!

---

