---
title: "hardy slow high cpu"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by nl87 on 2008-07-01
I just upgraded from gutsy to hardy and right away realized that hardy was very sluggish.  At first I saw that all my compiz effects were very slow but quickly realized that browsing the internet was slow too.  Htop showed that the cpu was very high whenever compiz effects took place.  So, I turned off compiz and it ran a little faster but the cpu was still high.  When I have a few applications open, its almost at 100%.  I'm a little skeptical about doing a clean install just because I have all my compiz and vmware configured.  Does anyone have any ideas on how I can run hardy normally like I did on gutsy?

Here's my htop while using compiz.  My laptop is only a year old and is pretty good.

---

### Post by nl87 on 2008-07-01
My Graphics card is also  Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) but it worked fine in gutsy.

---

### Post by Pumalite on 2008-07-01
Run:
sudo apt-get autoremove
See if it helps.

---

### Post by nl87 on 2008-07-01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This is what it gave me after I ran sudo apt-get autoremove. Didn't do anything.:(

---

### Post by Pumalite on 2008-07-01
I'm afraid that if you want real improvement, you'll have to save data and /home and do a clean install. The other thing is your card. Is it capable of Special Effects under the new system?. Find out in the Ubuntu site.

---

### Post by nl87 on 2008-07-02
Yea it is I checked.  I guess I will try clean install.

---

