---
title: "AWW so what whit the unity"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Riskexas on 2011-05-01
o what the hell why in ubuntu 11.4 (normal boot) there is no unity??:confused:?? why nobody solves this??:confused:??

---

### Post by Elfy on 2011-05-01
Hard to know what your issue is without any detail, but have you installed any graphic drivers available in sys - admin - additional drivers.

---

### Post by Riskexas on 2011-05-01
on after login i see my background but folders on desktop flickers. I read about that it is unity problem (i think its nautilus that doesnt start!!). EVRYthing was ok on ubuntu 10 but ubuntu 11.4 screw evrything!!!! IF this aint goin to be solved im out of linux FOREVER!!!!!

---

### Post by terrapin893 on 2011-05-01
As was mentioned earlier, this is generally due to the fact that you do not have any graphics drivers installed.

---

### Post by Riskexas on 2011-05-01
so how to make my drivers work properly?

---

### Post by kansasnoob on 2011-05-01
We first need to know what graphics chip you have so we need to see the output of:

```
lspci | grep VGA
```

If you can't get a working desktop ATM you may need to use a known working Live CD/USB to provide that info.

Just a basic hint, regarding comments like this:

> EVRYthing was ok on ubuntu 10 but ubuntu 11.4 screw evrything!!!! IF this aint goin to be solved im out of linux FOREVER!!!!!


We're all just volunteers here, and while we all understand frustration, you're more likely to attract help if you're polite :D

---

### Post by Riskexas on 2011-05-01
i think u need is this:
```
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200 Ultra] (rev a1)
```

---

