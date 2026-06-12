---
title: "New install of 18.04 Login loop; startx does work, but can't get gdm working"
date: 2019-03-10
forum: Installation &amp; Upgrades
---

### Post by brianmrowe2 on 2019-03-10
I have so many post on the login loop, and I have tried most of it.  I finally decided to re-install.  This machine was running 18.04 fine, but after some update and reboot, I started getting the login loop issues.  I did the new install, formatting the install drive and mounting my old /home drive while making a new user.
My new user can't login, but if I drop to command prompt (ctrl-alt-F3) and do a startx everything runs fine.  I tried to install lightdm, but then I get failed to start session.  I installed lightdm because GDM was crash/freezing as soon as I pressed login, saying authentication error maybe ( I stopped rebooting and clicking it.)  Its driving me crazy.  I can use the machine because startx works, but its really now ideal obviously.  Any help would be great.

---

### Post by brianmrowe2 on 2019-03-10
I removed lightdm, reconfigured gdm3 and rebooted, and I have the new user I created from new install looks like it worked.  The old user, still not work.

---

