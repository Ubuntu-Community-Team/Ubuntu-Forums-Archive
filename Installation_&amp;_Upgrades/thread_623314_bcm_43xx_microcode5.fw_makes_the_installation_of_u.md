---
title: "bcm 43xx_microcode5.fw makes the installation of ubuntu impossible"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by tico82 on 2007-11-25
Hi, i am pretty new here and so is my new laptop with the absolute disturbing vista premium. so i decided to change to ubuntu, but i can not install it, due to a failure called bcm 43xx_microcode5.fw not available or load fail.  i tried already quite a few things but nothing changes. i desactivated the network boot, i tried all the versions of ubuntu (the 7.10 with x64 and the normal) and the alternate version where i got stuck cause i couldnt find a way to create the necesseary partitions in the setup. i also read for hours and hours blogs and comments but the only solution i found was to add some orders in the boot menu. i already tried to noapic, pci=noacpi, nolapic and apci=off but i the installation always stops shortly after the moment when the the orange loading bar is complete. there are some more lines on a blackscreen with some loading parameters and (OK) on the right site until my favourit failure appears. 


if u have some good ideas let me know cause otherwise i will have to stay with vista... THX:)


My laptop is a acer travelmate 5520 and i guess that the failure has something to fo with the broadcom wireless adapter...

---

### Post by ruggersway on 2007-11-26
Broadcom wireless chipset - I have the same chipset but I don't believe I was forced to use it in order to install.  Are you able to get this to install at all?  You should be able to boot to the disk and run the install, you just won't have working wireless until you are able to install the bcm firmware.

Is this something you are attempting to do during the installation?

My installation was fine using a similar wireless the problem I had was when attempting to install using the bcm fwcutter script after installation.  I can explain my experience with that if you are to that point, but if your problem lies in actually getting the system to install we'll have to start there.

Live Cd?  Error during, after, or before installation?  I got the impression you couldn't boot from the cd  successfully, is that correct?

More info please, and I'll try to help.

-rugger

---

### Post by tico82 on 2007-11-26
> **ruggersway said:**
> Broadcom wireless chipset - I have the same chipset but I don't believe I was forced to use it in order to install.  Are you able to get this to install at all?  You should be able to boot to the disk and run the install, you just won't have working wireless until you are able to install the bcm firmware.

Is this something you are attempting to do during the installation?

My installation was fine using a similar wireless the problem I had was when attempting to install using the bcm fwcutter script after installation.  I can explain my experience with that if you are to that point, but if your problem lies in actually getting the system to install we'll have to start there.

Live Cd?  Error during, after, or before installation?  I got the impression you couldn't boot from the cd  successfully, is that correct?

More info please, and I'll try to help.

-rugger

i tried to but actually i cant even start or install ubuntu. it just always stops after the first ubuntu logo and the orange bar which slides from right to left. i cant even start it, thats correct. the safe graphics mode doesnt work either.

---

### Post by ruggersway on 2007-11-26
What are your specs on your computer? CPU?

What version iso's have you dl'ed and tried?

---

### Post by retrow on 2007-11-26
Is a manual switch off for your wireless card? If you do, then switch off the wireless and connect to your router (if possible) with a wired ethernet cable.

As far as boot options are concerned, in my case  adding **irqpoll** after **splash** in that kernel line solved the problem.

---

