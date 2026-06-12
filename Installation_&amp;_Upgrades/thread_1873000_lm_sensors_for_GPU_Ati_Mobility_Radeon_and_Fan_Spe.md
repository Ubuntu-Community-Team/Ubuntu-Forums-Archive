---
title: "lm_sensors for GPU Ati Mobility Radeon and Fan Speed"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by 1grouchy on 2011-10-31
I have problem with loading sensors for GPU and Fan Speed. When I run sensors-detect at the end I got this message:

[COLOR=#696969]To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

[COLOR=Black]When I type sensors in terminal i got only temperature of my CPU. In sensor applet I have temperature of CPU and HDD but GPU and Fan Speed is missing.[/COLOR]
[COLOR=Black]
What I need to do to got these temperature parameters working?[/COLOR]

[COLOR=Black]My graphic card is: ATI/AMD Mobility Radeon Series 4
Motherboard: [/COLOR][/COLOR]Toshiba NSWAA

Thanks in advance.

---

### Post by PhartSmellah on 2012-02-07
bump.

I have AMD Radeon HD 4550. other than that - all is the same. runnign "sensors-detect" gives only coretemp, and running sensors gives only CPU and HDD.

running ubuntu 11.04 64-bit on gnome 2 classic

help please?

---

### Post by PhartSmellah on 2012-02-07
update - 

(half-)success!
i've managed to connect my motherboard's sensors :D

i have a gigabyte z68 mainboard, so i used the standalone it87 driver:
[http://khali.linux-fr.org/devel/misc/it87/](http://khali.linux-fr.org/devel/misc/it87/)

from lm-sensors:
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

the other part of this issue still remains:
this fixed my problem with the mainboard sensors. still don't have the GPU temperature.

however, when i do
```
$ aticonfig --od-gettemperature
```
i get

```
Default Adapter - ATI Radeon HD 4550
                  Sensor 0: Temperature - 44.50 C
```

so that means i DO have reading from my card to the system.
how do i get this into lm-sensors?

---

### Post by PhartSmellah on 2012-02-08
solved completely :)

as it turns out, sensors only works with the open source ati driver!

i followed the instructions in [this link]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") to completely remove the proprietary driver and install the open source one. after a reboot, the card was being detected automatically - didn't even have to run  sensors-detect...

---

### Post by 1grouchy on 2012-02-10
Great job! :P

Regards.

---

