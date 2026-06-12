---
title: "Problem with Live USB"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by ignacioguevara on 2010-12-01
Hi
I have a problem with an Ubuntu 10.04 and 10.10 Live USB with a 2 gb persistency file.
I manage to install the OS and run it on an HP notebook. The first time I run the live USB I try to install the private drivers from Nvidia, but the update went wrong in both version of Ubuntu every time I try it. But... (there´s always a but) if I install Ubuntu 9.10 into the USB I´m able to update the video drivers without a problem.
There´s anything that I´m doing wrong?
I install the Live USB with the tool I found in the System menu.

Thanks in advance

ignacio

---

### Post by efflandt on 2010-12-01
When you use a bootable iso on USB you cannot update the kernel or video drivers because that is fixed in the squashfs file system that boots and loads before persistent data is mounted.  So what fails is initramfs attempting to create a boot image to a place that is read only.

You can add programs that run "after" booting, but should not try to change anything required for booting.  If you want to change video drivers or kernel version or anything else that happens before login, you either have to do a regular install, or roll your own iso with what you want already on it (more complicated).

---

### Post by C.S.Cameron on 2010-12-01
The standard drivers in a persistent instsall of 10.10 seem to work with Nvidia cards pretty good to me now, you can get dual monitors working, etc.

If you need to get Nvidia drivers for sure, you can do a Full install to flash drive just like to internal drive.
I would suggest disconnecting the internal drive prior to proceeding though.

---

### Post by ignacioguevara on 2010-12-04
Thanks both you for your answers. You  answers me these post  and another post I submit.
I would try to install the OS into a PC hard drive and see what happens

---

