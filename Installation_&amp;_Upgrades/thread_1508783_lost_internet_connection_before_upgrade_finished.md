---
title: "lost internet connection before upgrade finished"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by harDRain on 2010-06-13
Last night I was upgrading from 9.1 to 10.0 and went to bed before the upgrade was finished and my internet connection was lost before the upgrade was complete.  This morning I checked and saw that I had to do the 'partial upgrade' but it freezes when it asks me for my password.  I can't get past that point.  My internet connection also freezes.  What do I do?  Thanks.

---

### Post by karthick87 on 2010-12-08
Run the following commands in terminal,

```
sudo dpkg --configure -a 
``````
sudo apt-get update
```

---

