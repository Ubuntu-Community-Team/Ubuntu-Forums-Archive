---
title: "gnome not launching after upgrade"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by dayanandasaraswati on 2008-02-16
hello friends,
      I have a very pathetic problem. last night i upgraded my system from 7.04 to 7.10. The system worked perfectly fine for three reboots. Now when i boot my system Gnome is not starting. I get the login screen, and i type my login id and password then Gnome loads and it shows only my wallpaper and no icons, no taskbar, nothing of any sort. Onething very peculiar is that Ctrl+Alt+Left Arrow or Ctrl+Alt+Right Arrow shows the animation of changing between workspaces and also changes the workspaces. But in no workspace i get any sort of icon or anything. Its just blank. I logged out and logged in KDE and its working perfectly fine. But i don like KDE and i want my gnome back. I tried to reconfigure xorg. So i used the command 
> sudo dpkg-reconfigure xserver-xorg

I followed through all the procedures of reconfiguring and after reboot, things go worse. it says "ubuntu is working in low graphics mode as its unable to detect my graphics card settings". it gives me an option to configure. I clicked that button and configured but nothing works well.Now kde is working but with the worst ever resolution and graphics.

I dunno what to do..Plz help me. I cant reformat my machine as i have too much important data. I have Intel dual core,Intel 102GGC motherboard  1GB RAM, ATI on board graphics card.

---

### Post by Partyboi2 on 2008-02-16
Have you tried reinstalling ubuntu-desktop
from a terminal (ctrl+alt+F2)
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by Partyboi2 on 2008-02-16
With the resolution and graphics there probably be a backup copy in /etc/X11 which you could replace your current xorg.conf with.

---

### Post by dayanandasaraswati on 2008-02-16
Ya thank you loads.... This worked...But my desktop is a little slow and sloppy..Dunno why..But something is better than nothing...Your help worked...Thank you..

---

### Post by kostkon on 2008-02-16
> **dayanandasaraswati said:**
> Ya thank you loads.... This worked...But my desktop is a little slow and sloppy..Dunno why..But something is better than nothing...Your help worked...Thank you..

You could open a terminal and give
```
top
```
to see if any process is using too much resources.

EDIT:
Furthermore, since you have reconfigured your X server, open the *xorg.conf* file and check what driver is being used. If the VESA driver is being used, then that explains the slowness of your desktop. Reconfigure again your X server to select the ATI driver or install the proprietary FLGRX driver, if you like.

---

