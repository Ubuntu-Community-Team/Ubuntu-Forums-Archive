---
title: "unreliable CPU thermal sensor; monitoring disabled ..."
date: 2012-12-24
forum: Installation &amp; Upgrades
---

### Post by hedgehorn on 2012-12-24
I just installed 12.10 on my 64 bit amd 4 core machine and I get an error on boot that says " unreliable CPU thermal sensor; monitoring disabled ...
Is there a fix for this? Thanks in advance

---

### Post by Arnold86 on 2013-01-07
Probably this would help.
[B][https://wiki.archlinux.org/index.php/Lm_sensors#K10Temp_Module](https://wiki.archlinux.org/index.php/Lm_sensors#K10Temp_Module)
 
[/B]```
sudo rmmod k10temp 
sudo modprobe k10temp force=1
```

---

### Post by arashi256 on 2013-03-04
Well, the original poster never said thank you so I will - works for me, cheers.

---

### Post by Arnold86 on 2013-03-05
You're welcome.

---

