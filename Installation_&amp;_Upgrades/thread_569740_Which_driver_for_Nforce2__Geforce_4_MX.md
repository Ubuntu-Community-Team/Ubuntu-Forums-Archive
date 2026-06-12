---
title: "Which driver for Nforce2 / Geforce 4 MX???"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by mgrusin on 2007-10-07
Gutsy beta (and if you tell me to wait for 11 days, I don't think waiting will solve this problem).

Machine: Shuttle SN41G2, V1.  Nforce2 chipset, Geforce 4 MX (NV18) integrated graphics.  I am outputting to a TV via S-Video, BUT have a VGA monitor for setup if necessary.

After install, Ubuntu prompts to upgrade to restrictred driver.  Done, but on reboot restricted driver does not recognize above chipset (shows "manual configure" window, which only helps when I revert back to vesa driver).

Reinstall (sorry, don't know how to wipe driver issues)

Next, try using synaptic to install Nvidia "legacy" drivers.  Same issue as above.  Reinstall.

Look at Nvidia's site, which implies that there are two legacy drivers (and the one in Synaptic seems to be the one I don't want).  Manually install the other legacy driver (a pain; can't find the right module for this kernel, doesn't have the right kernel headers to compile itself, bleh.)  Finally get it to install. Reboot.  Crash.  Reinstall.

Sorry, but this is very frustrating (and for any Gutsy developers, my max resolution to TV is 800 x 600.  The graphical installer window does not fit on my screen.  Every continue/cancel button is hidden below the bottom edge.  I can get through it by guessing, but WTF?  Same in Feisty BTW).

So, what drivers do I need to install (preferably from Synaptic) to get the above graphics chips to work?
 
Thank you, -MG.

---

### Post by chicoicho on 2007-10-07
Dude use the Automatix 2 and install driver for you card!!

---

### Post by mgrusin on 2007-10-07
Thanks for the reply.  Any reason Automatix can do this while Synaptic cannot?  Do you have this graphics chipset?  What driver did you use (current or legacy?)

---

### Post by chicoicho on 2007-10-08
I have GeForce 5200 but crash, and now use onboard vga his intel.I have no many for new card.  :-k

---

### Post by dthiessen on 2008-01-23
I have the exact same onboard video. Can't find the driver either...hopefully this is fixed soon.

---

### Post by PmDematagoda on 2008-01-23
Are you able to use the GeForce Legacy cards by using the nvidia-glx-legacy package?

---

