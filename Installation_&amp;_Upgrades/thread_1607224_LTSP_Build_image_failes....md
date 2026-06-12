---
title: "LTSP Build image failes..."
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by xdarkness2 on 2010-10-27
Im trying to build the image for my thin client and get this error
when executing the following command: ltsp-build-client --arch i386

> 
.... normal stuff...
Processing triggers for ureadahead ...
Instellen van libdrm2 (2.4.21-1ubuntu2.1) ...
Instellen van libdrm-intel1 (2.4.21-1ubuntu2.1) ...
Instellen van libdrm-nouveau1 (2.4.21-1ubuntu2.1) ...
Instellen van libdrm-radeon1 (2.4.21-1ubuntu2.1) ...
Instellen van libudev0 (162-2.1) ...
Instellen van udev (162-2.1) ...
udev start/running, process 20192
Removing 'local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
**passwd: unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c255 is not authorized to change the password of root**
fout: installatie van LTSP-client werd onverwacht afgebroken


(sorry for the dutch locales)
Anyone know how to fix or resume from the console from here on.. ?

---

