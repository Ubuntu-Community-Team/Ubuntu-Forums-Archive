---
title: "Nomodeset as Default"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by WeeDavey on 2011-12-16
I admit to being a Linux 'newbie', (first effort was 9.04, now running 11.10), and it's now my main operational system , but.... why do I have aggravation every time I upgrade (and can Canonical please explain their reasons more openly why they change 'products in their distro), main gripe is graphics, I have a Nvidia graphics card and always have to interrupt the install to set the 'NoModeset' option before I can continue, can this not be made the default until install complete ?

---

### Post by dino99 on 2011-12-16
which card exactly ?
now the kernel directly deal with X, so no need of xorg.conf (except for special config: multi monitor, old crt, some tv)

so make some cleaning:

sudo rm /etc/X11/xorg.conf

from synaptic:
- remove/purge ALL the nvidia* installed packages
- reinstall: nvidia-current, nvidia-settings

close everything then reboot

---

### Post by WeeDavey on 2011-12-16
Card is a GTS250 in a Brand New 'Virgin' (64bit) system I have just built and STILL I have to interrupt and set NoModeset to get the install to see my monitor. Just had a thought ! have also loaded 11.10 on my 32bit test system with no problems, maybe a 64bit problem.

---

