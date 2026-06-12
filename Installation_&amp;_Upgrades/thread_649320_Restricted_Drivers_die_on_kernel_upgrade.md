---
title: "Restricted Drivers die on kernel upgrade"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by cacimar on 2007-12-24
I tried to fix a problem that turned out not too exist (recording sound)  much by downloading the latest alsa drivers and compiling them into a new kernel.  That killed all sound capability.  So I removed the custom kernel and discovered that booting to kernels below 2.6.22-14 restored sound.  After that discovery I removed packages related to that version. 

Now, every time I upgrade to that kernel, my sound and any restricted drivers are unavailable (wireless, usb hub)

Dell E1505


It seems the kernel upgrade is grabbing my mungery instead of the functional configurations still available when I boot to lower kernel versions.

Any ideas on how to undo my magic and get the latest kernel to allow restricted drivers and just use what prior kernel configurations used?

When I install 2.6.22-14, I include the restricted modules bit as well.

---

### Post by Pumalite on 2007-12-24
Did you try:
sudo apt-get install linux-backports-modules-generic

---

