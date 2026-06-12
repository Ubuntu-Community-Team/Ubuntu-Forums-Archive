---
title: "[SOLVED] X wont start - no screen found"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by jrtpaul on 2007-08-11
Hi

2 days ago i had some updates in Ubuntu (7.04 )so let them install. When i rebooted (can remember wether or not i had to because of the updates) and x failed to start. In the error messages i find at the end "Fatal error : no screens found". So i am thrown into termnai. After "sudo dpkg-reconfigure -phigh xserver-xorg", where i choose "nv" and 1280x800 as the resolution and type "startx" and i can get into GNOME. I open Restricted Drivers Manager and enable the nvidia driver. After i restart the computer i get the same error as before. I use the same method as before to get back into GNOME. Now if i open Restricted Drivers Manager a dialog tells me my hardware needs no restricted drivers. I reinstalled Feisty and this happens again. i am pretty sure this problem is caused by the updates. 

Any suggestions will be tried and any questions answered to try and rectify this problem.

Thanks!

---

### Post by jrtpaul on 2007-08-11
Ok - solved it myself.

i downloaded Envy, written by tseliot, and used the option "Install NVidia driver manually and chose 100.14.11 . That worked straight up - even made Resticted driver manager work properly too!

---

