---
title: "can not install updates Ubuntu 7.04"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by KakadoSantos on 2007-05-05
:) Hi everyone:

I upgraded from 6.10 to 7.04 without problem and I was able to download updates from Ubuntu servers until a couple of days ago.
This is the message that I get when trying to install updates:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Anybody have an idea what I need to do next to correct this problem and continue installing my updates as usual. Any help will be greatly appreciated. Thanks   :confused:

---

### Post by zvacet on 2007-05-05
**programs>accessories>terminal**

```
sudo dpkg --configure -a
```

---

### Post by KakadoSantos on 2007-05-06
Thanks zvacet for your help. It worked :) :) :)

---

