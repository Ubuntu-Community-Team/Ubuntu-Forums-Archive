---
title: "Usplash with custom kernel?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by sk545 on 2005-10-14
Can usplash be used with a custom (vanilla) kernel?  If so, is there a guide anywhere that will help me through the steps?

Thx.

---

### Post by sk545 on 2005-10-15
bump.

---

### Post by sjoh_64 on 2005-10-16
That doesn't seem to be much of a problem. I have kernel 2.6.13.4 running okay with bootsplash. Steps to reproduce:

1.) Fetch the vanilla kernel, untar/bz2/gz it.
2.) Use the configuration of your current kernel. It's found here: ```
/boot/config-`uname -r`
```
2.5) Install needed tools:
```
sudo apt-get install build-essential kernel-package fakeroot
```
3.) Make a kernel image and initrd: ```
make-kpkg kernel_image --append-to-version=-custom --revision=01 --initrd --rootcmd fakeroot
```
5.) Install the newly created .debs: ```
sudo dpkg -i name.of.deb
```
6.) Reboot

Usplash should still work just fine.

---

### Post by sk545 on 2005-10-16
alright, thx.  I'll give it a try soon. :)

---

### Post by seldenthuis on 2005-10-16
Make sure you have framebuffer support enabled and the vga16fb driver is installed. Usplash only works with that driver.

---

### Post by felipe on 2005-10-18
it works :)

you should post this as a mini-howto

---

