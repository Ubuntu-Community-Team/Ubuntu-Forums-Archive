---
title: "Nvidia Dual Monitors"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by ouchiko on 2005-08-12
Hi,

I've managed to setup dual monitors on an Nvidia card correctly.  Everything works fine using the specific nvidia options however on startup the login screen and subsequent desktop act as one huge monitor in such a way that expanding an application will fill all 2400 pixels of the screen, not the 1280 of one screen.

The way to solve this is to log off and back in again and screens are treated seperately and expanding apps only go to the size of the screen in use and the gnome taskbar exists in only one screen..  IS thier any way to make this happen on first boot/login without having to log out and back in again..?

Many thanks

P.S - I've only recently dumped Windows for ubuntu and I'd like to say it's impressive and I havent looked back.

---

### Post by BARAI127835 on 2005-08-12
Hi
I`m new to Unbutu.......Would you able able to help me on how to install the video drivers,I had downloaded the drivers fron Nvidia web site, but I cant seem to understand the instructions there have there to install, I pu the cd in but it doesnt give me an option to type what the instruction said on how to exe the install file, would you be able to help, please???

Thank you

Rick

---

### Post by thechao on 2005-08-15
Are you still having problems getting the Nvidia card to work? In a clean install of 5.04 (Hoary?) do this:
1) System -> Administration -> Synaptic Package Manager
2) Make sure the "Sections" button is selected in the lower left hand corner
3) Highlight "Miscellaneous - Graphical (restricted)" on the left hand panel
4) select on the right hand side:
        nvidia-glx
        nvidia-kernel-common
        nvidia-settings
5) press the "Apply" button
6) everything /should/ work, but... I have a custom xorg.conf file (in /etc/X11/) which I use, so I don't know if *that* file is set up correctly. The particulars of the xorg.conf file are dependent upon your particular monitor setup. Here's mine:
dual Samsung 19" LCD @ 1280x1024:
1) removed the line under "Section "Module"" that said "Load "dri""; your mileage may vary
2) under "Section "Device"", changed "Driver "nv"" to "Driver "nvidia"",
still in the same section, I added the lines:
Option "TwinView"
Option "MetaModes" "1280x1024,1280x1024"
Option "TwinViewOrientation" "RightOf"
Option "NoLogo" "True"
Option "RenderAccel" "True"
3) under "Section "Monitor"" I have "Identifier "SyncMaster"" (my monitor's family)
4) under "Section "Screen"" I have the DefaultDepth set to 24
etc.

The information is outlined in the README.text document provided on Nvidia's text--although that document is a bit long winded; night reading, y'know.

As a further post to the first user's question ... how /did/ you get the splash screen across both screens at login? That sounded kinda cool.

---

