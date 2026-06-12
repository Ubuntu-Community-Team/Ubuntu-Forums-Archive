---
title: "Lid switch &amp; low battery trigger problem [NC6000]"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by raido357 on 2009-04-16
Hi

I have a problem here with HP NC6000, actually it began from 8.04 version already, currently using 9.04.

Lid switch doesn't to nothing, even it's state doesn't change, although it will start working after i have hibernated my laptop and resumed it. It would be really nice to found a fix or something.

watch -n 0.5 cat /proc/acpi/button/lid/C138/state -> no change while pressing lid switch.

#dmesg | grep Lid
[ 3.601609] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[ 3.601782] ACPI: Lid Switch [C138]

Second problem I have (also earlier versions had it), that when laptop battery gets low or critical then system will not suspend/hibernate/shutdown, it  just drains the battery completely.

Edit: i enabled laptop-mode but at the moment i can't test, if it makes my laptop suspend on critical battery level.

Any help ?

---

