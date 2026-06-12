---
title: "nvidia driver installation kills X"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by kevpatts on 2010-11-09
Hey all,

I've seen may similar issues to mine, but some are different and others are identical, but have been resolved since in the repositories.

I install Maverick from CD, reboot, update via update manager, reboot, install nVidia driver via additional hardware gui, reboot and I can't get into X, I get tty1 instead with a text login prompt.

dmesg tells me:
```
nvidia: probe of 0000:01:00.0 failed with error -1
```

purging nvidia-* and deleting /etc/X11/xorg.conf means that I can get back into X, but without any hardware drivers.

I have both an onboard and PCI-E nVidia graphics adapters but my PCI-E one is primary.

---

### Post by dino99 on 2010-11-09
actual kernel directly deal with X, so xorg.conf is not needed by default

---

### Post by kevpatts on 2010-11-09
I realised that it's cause I have two nVidia graphics adapters installed. I removed the PCI-E one and it boots fine now.

---

