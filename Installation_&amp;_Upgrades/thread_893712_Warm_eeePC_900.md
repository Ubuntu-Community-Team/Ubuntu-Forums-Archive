---
title: "Warm eeePC 900"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by jcroblesemanuelli on 2008-08-18
I have installed eee-ubuntu on my eeepc 900.  It is working fine but I do notice that it runs a bit warm.  I came accrossthis thread [http://wiki.eeeuser.com/howto:overclockfsb]("http://wiki.eeeuser.com/howto:overclockfsb") on how to overclock the fsb and when I check the temperature via: ```
cat /proc/acpi/thermal_zone/TZ00/temperature
```
no matter what the temperature says, the fan speed via: ```
cat /proc/eee/fan_speed
``` is always set at 40.  Shouldn't the fan speed adjust depending on what the temperature of the laptop is?

---

