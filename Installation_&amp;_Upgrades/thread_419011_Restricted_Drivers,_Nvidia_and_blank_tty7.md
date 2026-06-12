---
title: "Restricted Drivers, Nvidia and blank tty7??"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Metz on 2007-04-22
I've just rebuilt my laptop with Fiesty, and added the Nvidia drivers through the Restricted Drivers Manager. When I reboot, as the GDM starts up, the screen goes blank. Everything is working, and I can actually login. I know this because I can hear all the startup sound effects. But the screen stays blank.

If I switch to tty1, login, remove the lock file (/tmp/.X0-lock), and 'startx'.....it all works fine, including apparently loading the correct NVidia drivers. Again, I know this because I get the full 1280*854 instead of the 1280*800 I get by default. 

Another odd thing though.... when I had it working previously (Edgy and Beta Fiesty)...when the Nvidia drivers loaded up, I used to get the colourful full screen Nvidia logo popup....doesn't happen now.

---

### Post by Big Ed on 2007-04-24
I still get the Nvidia screen popping up during the boot process in Feisty.  That' supposed to be the signal that the driver has loaded.  I wonder if your Nvidia drivers didn't install correctly.  Have you tried uninstalling and re-installing them?

Ed

---

