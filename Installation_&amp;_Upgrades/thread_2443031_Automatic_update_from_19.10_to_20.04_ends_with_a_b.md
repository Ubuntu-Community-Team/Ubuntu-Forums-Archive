---
title: "Automatic update from 19.10 to 20.04 ends with a black screen"
date: 2020-05-10
forum: Installation &amp; Upgrades
---

### Post by zombii2 on 2020-05-10
[COLOR=#242729][FONT=Arial][FONT=inherit]][FONT=inherit][FONT=inherit]I updated 19.10 to 20.04 using the automatic update system. The installation ended into just a black screen. No message was shown that the installation was complete. When I restarted using the power button on the computer it seems like Ubuntu 20.04 indeed has been installed anyway. Can I trust it has been installed properly although getting no confirmation message but only a black screen, or has anything gone wrong with the installation?[/FONT][/FONT][/FONT][/FONT][/COLOR][FONT=Arial][FONT=inherit]
[/FONT][/FONT]

---

### Post by Impavidus on 2020-05-10
Difficult to say if everything is OK. If you use the package manager, do you get any errors?```
sudo apt update
sudo apt upgrade
```If those commands run fine (and use the focal repositories), your system is probably OK.

---

### Post by zombii2 on 2020-05-11
Thanks for answer. Commands work fine (without errors) so hopefully things are OK.

---

