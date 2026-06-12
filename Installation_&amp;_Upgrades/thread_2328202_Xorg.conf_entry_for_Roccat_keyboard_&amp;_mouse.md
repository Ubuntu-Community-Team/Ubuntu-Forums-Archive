---
title: "Xorg.conf entry for Roccat keyboard &amp; mouse"
date: 2016-06-18
forum: Installation &amp; Upgrades
---

### Post by fettuohi on 2016-06-18
I have a HP 8640p laptop that I installed Ubuntu 16.04 on. I have the laptop connected to a docking station with an external Samsung 22 inch monitor. I have Roccat Ryos keyboard and Roccat Kone XTD mouse connected to the docking station. I have installed the roccat-tools from a ppa. Usually you need to add an entry to the xorg.conf file. But in my installation there isn't one under /etc/X11/. So do I need to add anything for my Roccat devices? There reason why I ask is that at the Ubuntu login screen the keyboard and mouse seems sluggish plus the keys don't light up. They do after login.

---

### Post by MAFoElffen on 2016-06-19
That is dated info. In the past input devices where added as lines in the xorg.conf file. That changed between 10.04LTS and 11.04. 

(Since 11.04) Is now handled as plug and play through another system. Xorg gets it's info from that other system, so lno longer defined in the xorg.conf file. If you check the xorg.X.log, you see were it queries and added, but uses those other system utils in that process.

Why? Is it not working with your device drivers?

---

### Post by fettuohi on 2016-06-23
OK, thanks for the info but the reason is that is that at the Ubuntu login screen the keyboard and mouse seems sluggish plus the keys don't light up. They do after login.

---

