---
title: "X-server failure post upgrade..."
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-03-14
I got a root user command prompt - what do I do next? Edit /etc/X11/xorg.conf? How?

Do I need to boot up a live CD?

---

### Post by Moozillaaa on 2010-03-15
Now I have X server is now disabled. Restart the gdm when correctly configured.

Help?

This does not work:
> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.broken

sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm restart 			 		
Screen flashes, and then stays at command prompt.

Help?

---

