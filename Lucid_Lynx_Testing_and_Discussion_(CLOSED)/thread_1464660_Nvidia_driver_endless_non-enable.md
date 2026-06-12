---
title: "Nvidia driver endless non-enable"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by regomodo on 2010-04-28
I'm trying to enable visual effects. Each time I try to I get the driver installer and enable windows. 

That's all well and good but each time I do the reboot I'm back to where I was beforehand.

I installed back in rc1 and I've been waiting for an update to finally fix this. Has anybody got any ideas (apart from manual install as I've got Funtoo for that) or is anybody else having this issue?

---

### Post by cariboo on 2010-04-28
Open a terminal and run:

```
sudo nvidia-xconfig
```

then reboot, to see if that solves the problem. Due to hardware detections problems, in some cases we still need an /etc/X11/xorg.conf.

---

### Post by regomodo on 2010-04-28
> **cariboo907 said:**
> Open a terminal and run:

```
sudo nvidia-xconfig
```

then reboot, to see if that solves the problem. Due to hardware detections problems, in some cases we still need an /etc/X11/xorg.conf.

I've already tried that in any case, The x-error dialog pops up on reboot. Also, 

> 
root@reg-desktop:~# modprobe -l | grep nvidia
kernel/drivers/video/backlight/mbp_nvidia_bl.ko
kernel/drivers/video/nvidia/nvidiafb.ko
root@reg-desktop:~# 


Additionally, an xorg.conf isn't needed and hasn't done so for a long time with the 8800gt.

---

