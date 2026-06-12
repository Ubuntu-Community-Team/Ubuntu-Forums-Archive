---
title: "Screen flashes"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by Vinger on 2005-06-07
Hello,

I wanted to try Ubunto linux on my computer, but i can't install it.
When i boot from the installationcd, i can choose to install (press enter) or install as server (server + enter).
When i try to install the software, my screen begins to flash. 
I tried to work with a live-version (cd and DVD) but that gives the same problem.

My PC has a partition of windows XP and on the other, there is SUSE 9.2 installed without problems.
motherboard: ASRock
processor: AMD athlon XP 3000+ (socket A)
screencard is on the motherbord.

Anyone an idea how i can install ubuntu?

---

### Post by mingus on 2005-06-07
It may be that the kernel initialization is having trouble reading your video card's driver and cannot execute the vesa framebuffer.

Boot from the install CD and at the : prompt, try
linux vga=normal

PS.  SuSE uses a different version of the kernel, which at least in my experience has been stronger with hardware detection.

---

### Post by Vinger on 2005-06-09
I tried to type 
linux vga=normal

but the problem remains.
it flashes a bit faster, 
(before about 1flash/secound, now 3 flashes/2secounds)

can i try something else?

---

### Post by mingus on 2005-06-09
Usually when this happens, it is because the installation kernel is having a problem detecting one of the hardware components.  To work around this, the kernel needs to be told to skip checking or trying to do some things.

When you boot from the installer, press F1 to see a menu.  F3-F7 show "arguments" that you can add to what you type at the prompt.  Review these.  Try:

:linux debian-installer/framebuffer=false debconf_debug=5 boot_debug=1

With this you are turning off framebuffer and using default vga, and asking for details of the boot process to be displayed - this may either correct the problem or at least show you where in the boot sequence (and possibly) why the problem is happening.

---

