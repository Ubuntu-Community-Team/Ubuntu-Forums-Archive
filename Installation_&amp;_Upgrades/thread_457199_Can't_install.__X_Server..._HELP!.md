---
title: "Can't install.  X Server... HELP!"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by huddy on 2007-05-28
Hey guys, I've been trying to create a dual boot since Christmas without any luck using 6.06, 6.10, and 7.04.  Each time I try to install, I arrive to a blue screen with a dialog box saying that my machine has failed to start the X Server and that it isn't set up correctly.

This baffles me because I've installed Ubuntu on other machines with trouble.

Here's my system specs
DFI Lanparty CFX3200-DR
AMD Opteron 170
2GB DDR 400
ATI X1900XT
2 SATA HD's in JBOD configuration.

Can anyone steer me in the right direction?

---

### Post by taurus on 2007-05-28
Try using the Feisty alternate CD to install it on your machine.

---

### Post by frozinfire on 2007-05-31
I had the exact same problem, and this is the only way I could fix it.

On the command line, type: 
sudo dpkg-reconfigure xserver-xorg

When you're asked about an auto detection for the video, select "no" and choose "vesa" on the list.
Go through the rest of the options, and choose to save the configs. When you're returned to the command line, type:
sudo killall -9 Xorg

You might need to run another line with "startx," but the graphicall installer will probably start right after the killall command.

I hope that works for you.

---

