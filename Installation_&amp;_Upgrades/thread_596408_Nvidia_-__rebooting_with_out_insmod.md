---
title: "Nvidia -  rebooting with out insmod?"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by kabads on 2007-10-29
I've just upgraded to Gutsy, with an old Nvidia GE force card. I have managed to get X working with Nvidia's installer script (including the proprietry driver). However, if I manually type 

```
sudo insmod /lib/modules/2.6.22-14-386/kernel/drivers/video/nvidia.ko
```

then I can start gdm as normal. But, when I restart the machine I have to type this again. 

I have nvidia in /etc/modules.

Any ideas how I can get gdm to start without the insmod each time? 

TIA
Adam

---

