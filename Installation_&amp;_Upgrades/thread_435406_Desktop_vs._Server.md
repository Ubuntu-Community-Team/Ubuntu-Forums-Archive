---
title: "Desktop vs. Server"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by dquam on 2007-05-06
Can I install both Desktop and Server CD's to the same partition?  I want to get all of the features.  Thanks.

---

### Post by aysiu on 2007-05-06
If you want to do that, use the Server CD and the Alternate CD, or the Server CD and just an internet connection. The Desktop CD would be useless to you.

Install the Server CD. Then log in and type ```
sudo apt-get update
sudo apt-get install ubuntu-desktop xorg gdm
sudo /etc/init.d/gdm restart
```

---

### Post by dquam on 2007-05-07
OK, thanks

---

