---
title: "(laptop) battery charging to slow"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by miegiel on 2009-10-13
Normally (yesterday too) my battery charges with something like 1700mA till it's 90% full and then the current starts to drop. At the moment it's charging with only 260mA and at that rate it will need to charge for 3 more hours for the last 20%. Oh no, it's dropping while I type (220mA and 4h to go).

I remember there was some ACPI stuff among the updates last night.

Any thoughts anyone ?

Going to check [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/) (maybe I should have done that 1st :))

@ 195mA and about 1000mAh to go till the battery is full :-\"

```
[COLOR="Green"]user@laptop:~$ cat /proc/acpi/battery/BAT0/state[/COLOR] 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            262 mA
remaining capacity:      4012 mAh
present voltage:         12298 mV

[COLOR="Green"]user@laptop:~$ cat /proc/acpi/battery/BAT0/info [/COLOR]
present:                 yes
design capacity:         5600 mAh
last full capacity:      4929 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  0 mAh
model number:            AS09D70
serial number:           5F07
battery type:            LION
OEM info:                SMP-SDI28

```

---

