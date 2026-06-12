---
title: "Fan issues on Macbook Air 6.2 Ubuntu 14.04"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by whatamidoingahh on 2015-03-24
Not sure if this is the right place to post this. 

I recently installed Ubuntu 14.04 and I am having some issues with the fans. Shortly after start up they ramp up to what sounds like full speed. I installed macfanctld when I run 

macfanctld -f this is what I get

Running in foreground, log to stdout.
Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 2000
    log_level: 0
Found applesmc at /sys/devices/platform/applesmc.768
Found 1 fan.
Found 33 sensors:
     1: TB0T - Battery TS_MAX Temp 
     2: TB1T - Battery TS1 Temp 
     3: TB2T - Battery TS2 Temp 
     4: TBXT - ? 
     5: TC0E - ? 
     6: TC0F - ? 
     7: TC0P - CPU 0 Proximity Temp 
     8: TC1C - ? 
     9: TC2C - ? 
    10: TCGC - ? 
    11: TCHP - ? 
    12: TCMX - ? 
    13: TCSA - ? 
    14: TCXC - ? 
    15: TH0A - ? 
    16: TH0B - ? 
    17: TH0C - ? 
    18: TH0F - ? 
    19: TH0R - ? 
    20: TH0V - ? 
    21: TH0a - ? 
    22: TH0b - ? 
    23: TH0c - ? 
    24: THSP - ? 
    25: TM0P - ? 
    26: TPCD - ? 
    27: TS2P - ? 
    28: TW0P - ? 
    29: Ta0P - ? 
    30: Th1H - ? 
    31: Tm0P - Battery Charger Proximity Temp 
    32: Ts0P - Palm Rest Temp 
    33: Ts0S - ? 
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual

The last 2 errors repeating. Is there a fix to this or a way to control the fans?

---

### Post by Tsepo_Joshua on 2015-03-24
have u tried cleaning the fan it might be dust

---

