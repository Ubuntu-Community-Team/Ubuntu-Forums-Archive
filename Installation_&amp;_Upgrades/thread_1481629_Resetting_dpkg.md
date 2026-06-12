---
title: "Resetting dpkg"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by dominiquec on 2010-05-12
I tried to install the Broadcom drivers on a 10.04 LiveUSB, but it borked during the initramfs setup portion.  I can live without wireless so I don't need to pursue this, however: 

Every time I install a new package through Synaptic, apt-get, or dpkg, it always attempts to configure the Broadcom driver.  And, of course, it fails.

What's the best way to reset dpkg so it doesn't do this anymore?

Thanks in advance.

---

### Post by dominiquec on 2010-05-13
Found the answer: copy over /var/lib/dpkg/status from a fresh LiveUSB installation.  (I just moved casper-rw to another location temporarily and booted the LiveUSB, copied over the status file, restored casper-rw, and copied the virgin status file over my setup's /var/lib/dpkg/status.)

Not perfect as the status file no longer remembers the other software that I installed, but otherwise workable.  I no longer get errors on initramfs.

---

