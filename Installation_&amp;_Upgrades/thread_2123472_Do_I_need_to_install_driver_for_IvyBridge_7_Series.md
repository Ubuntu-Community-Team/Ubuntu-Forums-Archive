---
title: "Do I need to install driver for IvyBridge 7 Series chipset?"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by callipso399 on 2013-03-08
The problem is that lm-sensors doesn't detect more than 2 sensors. It seems that drivers for chipset are not installed. 
Where I can get them? Is it already builtin in linux kernel?

System: Ubuntu 12.10. Dell Inspiron R15 / i7 / Mobile Intel HM76 Express Chipset.

Thank you.

---

### Post by Cheesemill on 2013-03-08
Does this make any difference...
```
sudo sensors-detect
```

---

### Post by callipso399 on 2013-03-08
Yes, I already run sensors detect (answered yes for all questions), but still get only 3 sensors:

user@user-inspiron:~$ sudo sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +48.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +48.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +46.0°C  (high = +87.0°C, crit = +105.0°C)

---

### Post by Kow on 2013-03-09
I do not believe the Dell Inspiron's have any more sensors than what you show. 'sudo sensors' on my Inspiron N4110 shows the exact same output as yours (temps are slightly cooler, however.) :)

---

