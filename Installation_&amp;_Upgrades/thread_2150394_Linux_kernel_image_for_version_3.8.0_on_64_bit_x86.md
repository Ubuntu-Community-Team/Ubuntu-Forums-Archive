---
title: "Linux kernel image for version 3.8.0 on 64 bit x86 SMP update failed"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by bcarney on 2013-05-31
Hi 
I just tried to install the recent (today) security update named "Lunix kernel inage for version 3.8.0 on 64 bit x86 SMP" part way through the install it failed saying it was corrupt. I ended up removing the package with synaptic package manager. After reboot I no longer have USB or Network support. On the Grub menu I boot to an older version (On now) and everything works fine. I ran software updater as a test and it is still telling me I need this security update? How do I repair this.

I forgot I am running ver 13.04 with KDE 4.0

Thanks in advance 
Brian

---

### Post by 2F4U on 2013-06-01
Try using a different mirror and see if you can download the update from there. The package may indeed be corrupt on your current mirror but if it also corrupt on a second mirror, something else may be wrong.

---

