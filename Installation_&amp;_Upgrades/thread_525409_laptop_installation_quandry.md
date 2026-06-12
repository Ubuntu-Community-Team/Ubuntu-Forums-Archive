---
title: "laptop installation quandry"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by cwm33 on 2007-08-14
I have a rather interesting problem that I'm hoping I can find a solution for.  I have a laptop (Acer Travelmate 2600) that I wish to install an operating system on, but the machine has no working optical drive, no floppy drive, and I highly doubt it would boot from USB as there is no boot to USB option in the BIOS/boot menu, plus the USB ports are a little flaky.

One thing I do have going for me though, is I am able to take out the hard drive, and use an external hard drive kit so that I can hook it up to my main tower (Ubuntu 7.04/XP Dual boot) and hopefully do some form of remote install.  What I have tried so far is installing Windows XP in a virtual machine environment, and then ghosting the image of the virtual drive over to the laptop hard drive.  That more or less caused a blue screen every time within about half a second of initial boot, so I'm guessing it doesn't agree with the motherboard drivers (probably also doesn't help that my main tower is an Athlon 64, and the laptop is a P4).

What would be my best option for installing Ubuntu under these circumstances?

---

### Post by theirishfrog on 2008-06-05
try using WUBI... it's a windows based installer that installs ubuntu on your selected drive just like any other windows program. this should allow you to install without a cd, usb or any other media.

Hope this helped!

TheIrishFrog

---

