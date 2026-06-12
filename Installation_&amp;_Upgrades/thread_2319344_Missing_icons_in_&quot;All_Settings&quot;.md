---
title: "Missing icons in &quot;All Settings&quot;"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by bicounet18 on 2016-04-03
Hello,
After mishandling Purge  with Xubuntu 14.04 and Xfce 4.10 , 
many icons in panel  "All Settings" window disappeared (network connection, language, printing, storm, additional drivers, user account ...)
How to restore?
After :
```
dpkg -l | grep buntu-desktop
ii  xubuntu-desktop    2.180     i386    Xubuntu desktop system
sudo apt-get install --reinstall xfce4
sudo reboot
```
These anamalies persist!
Thank you

---

