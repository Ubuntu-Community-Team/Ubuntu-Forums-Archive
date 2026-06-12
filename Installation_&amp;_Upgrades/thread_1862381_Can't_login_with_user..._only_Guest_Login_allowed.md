---
title: "Can't login with user... only Guest Login allowed"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by atentik on 2011-10-16
Damn with this 11.10. I was having some issue with frequent crash with my system after 11.04 -> 11.10 upgrade and try fixing it with no avail. After I rebooted the computer, I now cannot login anymore. I did ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` both by Ctl+Alt+F2 and recovery mode but nothing seems to work. I am now using the laptop in the Guest mode. I can't switch user either. Any help would be greatly appreciated.


Thanks.

Problem solved after removing .Xauthority

---

### Post by julianofischer on 2011-10-18
Thank you so much.
I had the same problem and solved the same way. :P

---

