---
title: "Bootup now asks for password and says incorrect"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by Rocknrod on 2015-07-16
Hi,
I have been running 14.04 for several months and have never had to put in any password on boot. I'm running MythBuntu with backend and front (Mythtv and Kodi) on same machine.
This morning when I started the machine it asked for a password I think it is just before the graphical console is displayed. It displays the correct username but will not accept my password. I'm sure the password is correct but are suspicious that something else has happened (software upgrade etc) as the boot normally goes straight through to load the frontend.
Other than my normal user I only have "mythtv" which I also tried but it rejected that password too.

Regards,
Rod.

further investigation from the root shell shows the user that was created for the mythbuntu install has no home directory. The user still exists and I can login from the shell. As I haven't used a terminal session for several days, this must have occurred via some script or update.

---

### Post by Rocknrod on 2015-07-19
Hi all,
Sadly this has happened again. I managed to get my install user up and running by creating a home directory and some required links to Myth backend. Next day the same but now the root filesystem is marked read-only and I cannot change it even as root. Therefore I can't create a home directory.
My only solution now is to start fresh

---

