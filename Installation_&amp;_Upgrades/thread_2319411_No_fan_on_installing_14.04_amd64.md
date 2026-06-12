---
title: "No fan on installing 14.04 amd64"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by maxson.elizabeth on 2016-04-03
I installed Trusty onto an older HP Pavilion dv6 laptop with no difficulties, and then after using it heavily for a day became uneasily aware I had not heard the fan.

I tried sensors-detect but all it gave me was coretemp, which was already inserted.

```

$  sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +60.0°C  


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +58.0°C  (high = +90.0°C, crit = +90.0°C)
Core 1:       +55.0°C  (high = +90.0°C, crit = +90.0°C)

```
```
$ ls /proc/acpi
ac_adapter  battery  button  wakeup

```

I had the hope that perhaps the problem was in the BIOS, and managed, with a great deal of swearing, to flash the most recent on the manufacturer's website, but have noticed no difference.  There *is *a setting in the BIOS for "fan always on" which I tried disabling, in case that made a difference, which it didn't.

Last time I had fan troubles I had to decompile ACPI, but I have the impression that is no longer recommended?

I'm hoping I overlooked something obvious, but I'll take anything.

---

### Post by X-RED_Tech on 2016-04-04
If the hardware is faulty (most likely) there's nothing you can do in BIOS or the OS that will change that.
You can confirm that by installing Windows or just recovering the factory installed OS.
Nevertheless the temps you posted are normal.

---

### Post by yoshii on 2016-04-04
I don't know anything about decompiling, but it seems to me to likely be an ACPI issue.  
Unfortunately, I don't know how to fix that.

---

