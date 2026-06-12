---
title: "Asus EPU-Six Engine substitute on Ubuntu"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by radocha on 2010-02-08
Hey

Does anyone know any software or tricks how slow down cpu. The aplet on top panel whose control cpu freq allow set only 2Ghz. On windows thanks to EPU-Six i can for example set 1,8Ghz and automaticly vcore drop to 0,967V. On ubuntu the lower value is 2Ghz and 1,1V.

I have Asus P5Q PRO on P45 chipset and Core 2 Duo E8400 on Ubuntu 9.10

---

### Post by mutha88 on 2010-02-10
I have the same problem. I have ASUS P5Q motherboard, but with a lower CPU model - Intel Core2Duo E2160.

The FAN is very loud, when I'm not using EPU-6 under Linux... Tried to install it with Wine, but nothing happen... So how can I (we) manage the CPU frequencies/fan usage and so on?

---

### Post by radocha on 2010-02-15
seems no one know how to resolved this problem :(

---

### Post by buzucan on 2010-05-03
any fix yet?

---

### Post by zzhao on 2010-05-26
I'd also like to have something similar with ASUS EPU Engine in ubuntu. When I run this program in Windows, I can immediately tell the difference in the noise made by the fan. It would be nice to also enable this feature in Ubuntu. At this moment my fan is running always at full speed and it is very annoying.

---

### Post by zzhao on 2010-05-29
Hi there. Just found out some settings in BIOS very helpful. Not sure if you also use the same mainboard. Mine is ASUS P7P55D-E LX. In BIOS->Power->Hardware Monitor there are settings called CPU Q-Fan. It can be set to standard, silent, turbo, and manual. This immediately changed my system to a very quiet one. I set my fan to 60% when idle and I can see from 'sensors' in the terminal that the fan speed drops to 1260 RPM:

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +0.86 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:      +3.36 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.06 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.43 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     1259 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =  600 RPM)
CPU Temperature:    +38.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:     +38.0°C  (high = +45.0°C, crit = +75.0°C)

---

### Post by grigio on 2010-07-20
+1 somebody should report it on asus forum..

---

### Post by mutha88 on 2011-02-06
I have ASUS P5Q motherboard with EPU-6 too. I'm under Windows XP right now, but after 2-3 weeks I'll go back in Ubuntu and I'll test the methods, described in this topic and report, if there are problems.

**Thank you! **


P.S: And ASUS suck... how can they DON'T support ANY Linux?! This is so lame... Won't buy ASUS motherboard again that's for sure...

---

