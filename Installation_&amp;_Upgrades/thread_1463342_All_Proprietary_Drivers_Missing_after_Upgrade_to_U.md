---
title: "All Proprietary Drivers Missing after Upgrade to Ubuntu 8.04.2, kernel 2.6.24-27-lpia"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by spalmer8 on 2010-04-26
I did open a bug for this as well:
[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/570449?comments=all](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/570449?comments=all)

After upgrade to to Ubuntu 8.04.2, kernel 2.6.24-27-lpia all proprietary drivers are gone.

Therefore, I cannot use wireless, webcam, sound, usb, etc... making work next to impossible.  

Does anyone know how to correct this easily and quickly so I am effective at work?

Thanks!

---

### Post by snowpine on 2010-04-28
Welcome to the forums!
The quick fix is to reboot and select your old kernel from the Grub boot menu. Hopefully that will give you a working computer while you troubleshoot the problem with the new kernel.

Installing the [dkms]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support") package might prevent this problem with future kernel updates.

---

