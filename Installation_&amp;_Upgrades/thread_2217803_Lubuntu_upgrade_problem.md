---
title: "Lubuntu upgrade problem"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by rdh61 on 2014-04-18
Hi,

My system informed me that a new version of Lubuntu (14.04) was available, so I started the automatic upgrade. Unfortunately the power in my house cut out during the upgrade, so it was not completed. Now my computer still boots into 13.10 but with all the software sources changed (to trusty). It still informs me that a new version is available, but when I try to upgrade the GUI hangs on "Fetching file 88 of 106" and does not proceed from there. What can I do?

Many thanks.

---

### Post by bapoumba on 2014-04-18
If you are sure all your software sources are changed to trusty, please open a terminal and run :
```
sudo apt-get update
sudo apt-get upgrade
```
Paste any error you get here.

---

### Post by rdh61 on 2014-04-19
Thank you. Having done that, I have upgraded successfully. No major errors noted. The only problem I've noticed so far is that chromium is broken (see my new thread: [http://ubuntuforums.org/showthread.php?t=2217965&p=12993135#post12993135](http://ubuntuforums.org/showthread.php?t=2217965&p=12993135#post12993135) ).

---

### Post by bapoumba on 2014-04-19
Glad to see you fixed it. Please mark your thread as solved (under Thread Tools), thanks!

---

