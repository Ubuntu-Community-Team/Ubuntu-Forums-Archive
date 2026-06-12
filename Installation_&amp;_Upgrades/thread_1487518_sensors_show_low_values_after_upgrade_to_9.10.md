---
title: "sensors show low values after upgrade to 9.10"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by kriebel on 2010-05-19
Guru's

After the upgrade from 9.4 to 9.10 (32 bits) the values of the cores are lower (even 8 or 9 degrees) than what they used to be (at least 40). sensor-detect en sensors was running ok. Anyone familiar with this issue?

sensors output:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +11.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +14.0°C  (high = +100.0°C, crit = +100.0°C)  


Thanks for any help!

Rgds, Kriebel

---

### Post by mörgæs on 2010-05-19
> **kriebel said:**
> 
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +11.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +14.0°C  (high = +100.0°C, crit = +100.0°C)  


If this means that the temperature is supposed to be 11 and 14 °C, I don't think you should trust the sensors...

---

### Post by kriebel on 2010-05-19
Mörgæs,

Thanks for your reply. The interesting thing is that on 9.4 the sensors gave higher (more realistic) values. That's why I'm thinking about a software issue.

Rgds, Kriebel

---

### Post by mörgæs on 2010-05-20
On my machine the same happens. Hddtemp shows a temperature of 30-something (Celsius) right after the boot, for example. I have not found a way of correcting this.

I use the sensors for watching the changes, not the absolute temperature.

---

