---
title: "Upgrade 8.04 -&gt; 8.10 Failure"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by solarwind on 2008-11-02
Hey all,

I tried to upgrade my system from Ubuntu 8.04 to 8.10 and the upgrade app froze. I was forced to kill the application and now my system is left in a broken state. Trying different combination of apt-get options (autoremove, -f install, dist-upgrade) didn't improve the situation. How do I fix my system? I don't even think my system is Hardy or Intrepid anymore, it's probably stuck somewhere in between.

---

### Post by Partyboi2 on 2008-11-02
Have you tried in order
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
``` If that doesnt work then you may have to bite the bullet and do a clean install.

---

