---
title: "NVidia weird characters and garbled display temporary fix"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by roberty82 on 2013-11-15
Hello linux world, I know I'm far from the only one who has trouble dealing with the weird characters and garbled display in the recent GeForce proprietary drivers. I wanted to suggest the solution I found.

Keep in mind you have to reboot if you need to restart the X server itself completely. Install KDE Display Manager (sudo apt-get install kdm), and select "kdm" as the default display manager when prompted. Then go into /etc/kde4/kdm and edit "kdmrc" as a sudo or root user with your favorite editor (either "sudo gedit /etc/kde4/kdm/kdmrc" in X or "sudo vi /etc/kde4/kdm/kdmrc" in the console). Look for the X-authorization options.

This is where Nvidia needs to work on their driver support - they obviously did a terrible job with the X-authorization configuration. When the Nvidia card needs a new X-authorization, it seems to think it needs to restart the card. Here are the X-authorization options I changed:

AuthComplain=False
Authorize=False
ResetForAuth=True

[http://docs.kde.org/cgi-bin/desktopdig/search.cgi?show=stable/en/kde-workspace/kdm/kdm-files.html&collection=en&include=stable&q=kdmrc](http://docs.kde.org/cgi-bin/desktopdig/search.cgi?show=stable/en/kde-workspace/kdm/kdm-files.html&collection=en&include=stable&q=kdmrc) has a list of the options.

I really hope Nvidia does more work on their proprietary drivers. The "nouveau" drivers don't understand multi-head (I have a GeForce GTX 630 - VGA, DVI, and HDMI), and don't seem to understand hi-res real well either. I put this solution out so those of you with GeForce cards can hopefully get things working.

---

