---
title: "acpi temperature and fan data not available"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2006-08-03
I may have done something outside the rules: I moved a working Ubuntu system from an AMD-64 motherboard to a Pentium-D motherboard (i.e. I moved the hard disk). The system works fine, except for the following: no fan or temperature data is available. The motherboard does regulate the fan speeds based on cpu and case temperatures, but this has nothing to do with the OS.

command and results:

# acpi -t
No support for device type: thermal

The /proc files indeed have no data.

Should I re-install Ubuntu from scratch on this motherboard?
The board is an Intel D975XBX with the 975X chipset.

---

### Post by rklauco on 2006-10-15
I am facing the same problem on SiS 735 mainboard.
Prevous version of Ubuntu 5.10 worked, version 6.06 server simply reports no support for thermal :-(

---

### Post by markba on 2006-12-17
> **rklauco said:**
> I am facing the same problem on SiS 735 mainboard.
Prevous version of Ubuntu 5.10 worked, version 6.06 server simply reports no support for thermal :-(

This bug is filed under:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/56785](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/56785)

---

### Post by saltydog on 2007-04-18
The same problem here. I have switched my disks from an AMD motherboard to a Pentium 4 (3ghz HT) motherboard (Asrock) and I have lost all thermal information. As this is my dapper server, I am quite worried about its temp and fan activity.
I don't really think the bug in launchpad is related to this. I am afraid that switching hard disk from a configured AMD motherdoard to a Pentium one should require some configuration tuning, but I don't know how.

---

