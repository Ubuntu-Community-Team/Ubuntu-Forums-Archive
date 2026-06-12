---
title: "Xubuntu Installation Problem: Failed Due to Unknown User ID"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by Aspen95 on 2010-08-03
Hi, 
Whenever I try to install Xubuntu onto my really old computer (not this one), it goes to a screen that shows nothing except the Xubuntu logo and the name. After a bit, my monitor falls asleep, and I am unable to wake it back up.
If I press enter while at this screen, it brings up the error message in the title. The same thing happens with all the options I try to press.

Can anyone help me out?

---

### Post by anglican on 2010-08-04
> **Aspen95 said:**
> Hi, 
Whenever I try to install Xubuntu onto my really old computer (not this one), it goes to a screen that shows nothing except the Xubuntu logo and the name. After a bit, my monitor falls asleep, and I am unable to wake it back up.
If I press enter while at this screen, it brings up the error message in the title. The same thing happens with all the options I try to press.

Can anyone help me out?Can you boot to a login in "Recovery" mode. If that works try ```
sudo service gdm start
``` I had similar issues on an old PC and found that this way booted to the desktop and then installing latest updates solved the problem.

H

---

