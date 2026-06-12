---
title: "live cd freezes on startup"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by superspak on 2006-12-18
i put in the edgy live cd 6.10, and it freezes on startup, the bar goes almost all the way to the end then the screen changes to a weird blurry color and a green line is under it, i installed dapper previously with xgl, and the drivers were for a nvidia, and i changed to ati and i just used partition magic to delete the ubuntu because it gave me errors, so i need help to get this to work, i have a amd x2 4200, ati x800, gigabyte motherboard

---

### Post by aberry5555 on 2007-01-02
Hi, I don't know how to fix this myself but I have the same problem as you. Is your GFX card a dual head PCI-E? I am pretty sure it is ubuntu not being able to start X but also not providing anyting in stead of the GUI. I also have this problem on PClinuxOS but, luckily, on that distro it will just tell you xorg cannot start and to manually configure the video drivers. For PCLinuxOS I use the radeon(FBdev) rather than radeon(GNU) or radeon(FGLRX) to start off with then I get the newest proprietary drivers from the ATI website (these seem to work absolutely fine). If you can find out how to make edgy or other start up with a self-specified driver please let me know :-D .

---

### Post by wpshooter on 2007-01-02
> **superspak said:**
> i put in the edgy live cd 6.10, and it freezes on startup, the bar goes almost all the way to the end then the screen changes to a weird blurry color and a green line is under it, i installed dapper previously with xgl, and the drivers were for a nvidia, and i changed to ati and i just used partition magic to delete the ubuntu because it gave me errors, so i need help to get this to work, i have a amd x2 4200, ati x800, gigabyte motherboard

Did you try booting with safe video mode parameter ?

If that does not work would suggest that you download and try the ALTERNATE installation CD.

Good luck.

---

### Post by aberry5555 on 2007-01-02
If the problem's the same as with mine it doesn't seem to make any difference at all :S

---

### Post by aberry5555 on 2007-01-03
[https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)
This is the walk-through on how to get around the problem.

---

