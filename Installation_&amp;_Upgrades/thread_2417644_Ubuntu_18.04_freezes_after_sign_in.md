---
title: "Ubuntu 18.04 freezes after sign in"
date: 2019-04-25
forum: Installation &amp; Upgrades
---

### Post by Bazman on 2019-04-25
I have a new build PC.

I7-8700  
Asus prime z390-a  
GeForce rtx 2080  
8gb ram 
2tb m2  
2tb hard drive (not currently connected during ubuntu install).

After a couple of attempts I managed to install ubuntu.

However after I restarted it now seems to freeze after login.

After researching it it appears this may be a problem with the nvidia drivers.

Ubuntu 14.04 LTS crashes after login

The suggested solution is to install these drivers but how can i do this if I can't log in?

---

### Post by similar2 on 2019-04-26
Try switching to a tty:

1. Press Ctrl+Alt+F2 to switch to tty2 and enter your credentials.
2. Then type this command (just to be sure): sudo apt purge nvidia*
3. Install the Nvidia drivers with: sudo apt install nvidia-390
4. Reboot your system with: sudo reboot

---

