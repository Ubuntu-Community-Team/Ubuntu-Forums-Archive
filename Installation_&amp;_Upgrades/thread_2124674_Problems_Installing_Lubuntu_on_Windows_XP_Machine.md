---
title: "Problems Installing Lubuntu on Windows XP Machine"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by bdylan616 on 2013-03-11
Hi everybody,

I'm trying to install Lubuntu 12.10 on my old eMachines XP computer, but for some reason whenever I try to boot from the USB that I created (I've created one with LinuxLive and another with UNetbootin) it tells me there's an "invalid boot.ini" and then it boots from the hard drive. Does anybody know exactly what the problem is? Thanks, I really appreciate the help.

---

### Post by Mark Phelps on 2013-03-11
Can we presume that XP does not work?  IF that's the case, this looks like it's skipping the USB stick and going straight to the hard drive.

If this machine if 5 years old, or older, there's a strong possibility that it does not BOOT from a USB stick.  If you have a manual, you could check that and see,

Also, with some PCs, you press F12 to get a one-time-boot-menu, if your works that way, see if there is something like USB-HDD in the list.  That is what yhou should be selecting.

Linux does not use boot.ini, so there is no reason for that file to exist on a boot USB you made from a Linux download.

---

### Post by bdylan616 on 2013-03-12
Yup, that was the problem. I had set the BIOS to boot from the removable disk, but I didn't realize that the only disk it could boot from was a floppy disk. I had to use a CD to install it instead. Thanks!

---

