---
title: "Desktop Effects errors"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by Liamkerrigan on 2007-08-22
hi there after recently installing Ubuntu 7 i went into desktop effects and downloaded some new update onto it and it told me to restart and now ever time i turn it on a boot onto Ubuntu 7 it comes up with a message saying "failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view that x server output to diagnose the problem?" (i clicked yes) and it says stuff like "failing to initialize the nvidia graphics device." and it just wont do anything. it lets me "login" then only stay on the same black screen and gives me a command line.. What do i do, please help me! cheers :(:(

---

### Post by tzulberti on 2007-08-22
You should use the command: "sudo dpkg-reconfigure xserver-xorg" to reconfigure X11. 
First try using nvidia driver.
To start the login use: "sudo /etc/init.d/gdm restart" (if using kde/kubuntu use kdm instead of gmd).

If it does not appears, then re-run "sudo dpkg-reconfigure xserver-xorg" and chooser nv as the driver. Then restart gmd.

If that work, look at the x11 log file in /etc/X11/ and post it here...

---

### Post by Liamkerrigan on 2007-08-22
hi, wow tzulberti that worked great, i got back into Ubuntu then i downloaded envy installed the correct nvidia drivers. its beautiful, couldn't of done it without ya mate. cheers :):)

---

