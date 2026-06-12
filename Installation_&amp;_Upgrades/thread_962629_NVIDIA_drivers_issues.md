---
title: "NVIDIA drivers issues"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by TheKing.j2 on 2008-10-29
when i installed ubuntu i installed the NVIDIA 3d graphics drivers and was running at 1280x1024. I installed the sensors applet to monitor the temperatures of my chips and when i rebooted the graphics driver would not enable. the screen reset to 800x600 and will not offer alternative options. Does anyone know how i can get my drivers working again. (i can live without the sensors applet)

---

### Post by kingtaurus on 2008-10-29
I think we might need some more details of the situation. Could you post the following (hopefully we will be able to debug this):
/etc/X11/xorg.conf
/var/log/Xorg.0.log
/var/log/Xorg.0.log.old
/var/log/dmesg

and the responses from the following commands:
uname -a
lspci
lsmod | grep nvidia

---

