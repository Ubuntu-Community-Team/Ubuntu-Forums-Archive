---
title: "Conky &amp; lm-sensors"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by geidorei on 2011-06-08
Hi - have looked through forums but cant seam to find an answer.

Have installed etc lm-sensors - all wen aok: output from sensors is:

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.24 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.26 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +5.04 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.25 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    1188 RPM  (min =  600 RPM)
CHASSIS FAN Speed:   0 RPM  (min =  800 RPM)
CPU Temperature:   +30.0°C  (high = +60.0°C, crit = +95.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (high = +86.0°C, crit = +100.0°C)  


However, Conky doesnt display any temp data:

Conky temp settings:
CPU - ${execi 60 sensors | grep -A 0 'temp2' | cut -c15-21} ºC
HDD - ${execi 60 sensors | grep -A 0 'temp1' | cut -c15-21} ºC

Also, how when I can get this to work, do you get temp of a second hard disk?

EDIT: on 11.04 Natty

Thanks folks, Karl.

---

### Post by LoREZ on 2011-06-10
I was having a similar problem, although I was using a different approach.  You may want to try the $platform variable.  But I got your syntax to work for my system.  It may be that you are missing the space between the "-c" option and its argument:

Yours:
```
CPU - ${execi 60 sensors | grep -A 0 'temp2' | cut [COLOR="Red"]-c15-21[/COLOR]} ºC
```

Mine:
```
CPU - ${execi 60 sensors | grep -A 0 'temp2' | cut [COLOR="Red"]-c 15-21[/COLOR]} ºC
```

Now, I couldn't just copy and paste your statement to make it work, even if I added the space later, because my sensors output is different:

```
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +0.86 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:      +3.41 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:        +5.18 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:      +12.04 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:     2008 RPM  (min =  600 RPM)
Chassis1 Fan Speed:   0 RPM  (min =  600 RPM)
Chassis2 Fan Speed:1416 RPM  (min =  600 RPM)
Power Fan Speed:   2376 RPM  (min =    0 RPM)
CPU Temperature:    +35.5°C  (high = +45.0°C, crit = +45.5°C)  
MB Temperature:     +36.0°C  (high = +45.0°C, crit = +46.0°C)
```

Therefore, I did this:

```
CPUtemp: $alignr${execi 60 sensors | grep 'CPU Temperature' | cut -c 22-28}
```

Which gives me just the temperature including the Celcius symbol:
```
CPUtemp:       35.5 ºC
```

Don't know if that helps, but you ended up helping me.  Thanks!

---

### Post by geidorei on 2011-06-12
Hi - awesome - temp on CPU now works. As a note moving the C doesnt make any difference.

Any idea about HDD temp? so far ive tried following:

${execi 60 sensors | grep -A 0 'temp1' | cut -c 15-21} ºC
${execi 300 nc localhost 7634 | cut -c 29-30 ;}C

And nowt is showing up.

Thanks.

---

### Post by LoREZ on 2011-06-12
I've learned a little bit since my last post, so perhaps I can help, although it will probably only point you in a direction rather than actually answering the question.

Looks like there are at least four different ways to get sensor output in conky: [FONT="Courier New"]${platform}[/FONT], [FONT="Courier New"]${i2c}[/FONT], [FONT="Courier New"]${hwmon}[/FONT], and [FONT="Courier New"]${execi}[/FONT]/[FONT="Courier New"]${exec}[/FONT].  I've moved to the [FONT="Courier New"]${hwmon}[/FONT] variable, instead of the previous [FONT="Courier New"]${execi}[/FONT].  It seems it is lighter on system resources and easier to use as well.  These are my sensor references in my conky.conf:

```
${offset 5}CPUfan: $alignr${hwmon fan 1} RPM
${offset 5}MBtemp: $alignr${hwmon temp 2}°F
${offset 5}CPUtemp: $alignr${hwmon temp 1}°F
```

It doesn't say which temp or fan is which, although you may be able to puzzle this out by correlating temps/rpms inside your BIOS, if it is sufficiently recent.

I hope that helped some.

---

### Post by geidorei on 2011-06-15
Hi - thanks for info will have a go.

---

