---
title: "USB doesn't work in newer kernal (Feisty)"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by DrQuincy on 2007-04-25
After I upgraded to Feisty from Edgy a new kernel version appears in Grub.  If I boot to the newer kernel none of the USB ports work.  It works fine on the older kernel though.

P.S. does it matter too much what kernel version you use?

---

### Post by sharke on 2007-04-25
It should work .
Please post output of command lsusb  (L lower case)
Todo in a termanal enter lsusb.
Regards 
Sharke

---

### Post by Smitty5k on 2007-04-26
I am having the exact same problem.

Boot from the Live CD for 7.04, USB mouse and keyboard work
Boot the older Kernel (installed on a second hdd), USB mouse and keyboard work.
Boot from the fresh install of 7.04 and USB mouse and keyboard do not work.(the USB keyboard even works in GRUB but once Ubuntu loads, it no longer works)

I'm at work so I don't have access to the system(I can post the output later), but when I run lsusb both the mouse and keyboard DO show up in the output from the command.

I'm also going to try a USB flash drive tonight and see if it automounts.

---

