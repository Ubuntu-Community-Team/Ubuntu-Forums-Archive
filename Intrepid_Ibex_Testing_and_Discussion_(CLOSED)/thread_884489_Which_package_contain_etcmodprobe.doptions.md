---
title: "Which package contain /etc/modprobe.d/options?"
date: 2008-08-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by damagedspline on 2008-08-09
Finally [https://bugs.launchpad.net/bugs/84159 ]("https://bugs.launchpad.net/bugs/84159") was solved in Interpid, but an update is also required for /etc/modprobe.d/options.

On which package should I open a bug?

echo "option acerhk autowlan=1" >> /etc/modprobe.d/options
 
$ cat /var/lib/acpi-support/*-*
R01-A1I
FUJITSU SIEMENS
AMILO A1650G
-1


Now that the acerhk patch is included a similar fix is required for FSC LI1718 aswell:
echo "options acerhk force_series=6805 autowlan=1" >> /etc/modprobe.d/options

---

### Post by dinxter on 2008-08-09
"dpkg -S /etc/modprobe.d/options" shows,
module-init-tools: /etc/modprobe.d/options

so it should be module-init-tools i suppose though i could be wrong obviously :)

[https://bugs.launchpad.net/ubuntu/+source/module-init-tools](https://bugs.launchpad.net/ubuntu/+source/module-init-tools)

---

