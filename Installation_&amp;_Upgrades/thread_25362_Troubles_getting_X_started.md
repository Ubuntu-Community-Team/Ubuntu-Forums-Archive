---
title: "Troubles getting X started"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by peter.nilsson83 on 2005-04-09
Writing this in the text-browser now, so bear with me :)

I'm having troubles getting X to start.
After install, when trying to get into X the screen blinks 3 times and 
the x-server says it's having problems starting. It shows me the log 
saying that there's no screens. 
and then goes into the command line. 
I'm gonna try to get the log-file attached in some way, so maybe someone 
can help me.
My computer:
DFI LP Ultra-D S939
A64 3000
256M RAM
ATI RX700Pro 128M
200GB Maxtor
Samsung SyncMaster 753s Monitor

---

### Post by humanity_to_others on 2005-04-09
Maybe you should manually enter your monitor's vertical and horizantal refresh rate.

---

### Post by c_dog on 2005-04-10
Don't use a ATI on my desktops (just laptop), but I have a feeling the non-proprietary AIT driver doesn't support the PCI-E ATI cards. like the X800, X700, or X300 yet. You'll probably need to get the proprietary ATI driver for X.org 6.8 from ATI website and install it. The 3 reboots is just the X server trying a few options to squeak you by under VESA, but it appears that isn't working and xorg can see your card in PCI slot 6 but can't load the driver for it.

---

