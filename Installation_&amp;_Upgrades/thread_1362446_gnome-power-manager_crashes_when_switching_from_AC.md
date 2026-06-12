---
title: "gnome-power-manager crashes when switching from AC power to battery"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by jrnymn on 2009-12-23
Hey guys,

When my laptop power switches from AC to battery the gnome-power-manager crashes. Also when I launch the gnome-power-manager while on AC it runs fine until a switch from AC to battery happens. But when I launch the gnome-power-manager while on battery it crashes again. After searching the net and trying to fix it with no success, I am only left with the trace I got after launching the gnome-power-manager with --verbose command, which I have attached. 

Have tried this on both Jaunty and Karmic, same problem.

Battery details:

$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      10800 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 540 mAh
design capacity low:     378 mAh
capacity granularity 1:  162 mAh
capacity granularity 2:  10260 mAh
model number:            Primary
serial number:           
battery type:            LION
OEM info:                Hewlett-Packard

Any kind of help would be appreciated.

Thanks.

---

