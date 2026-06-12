---
title: "Can't create LVM Groups with my md-devices..."
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by scheuri on 2006-06-08
Hi to all

We have here two IBM IDE harddisk with each 80 Gbyte (same type of hardware).
For installation, or actually starting with it, we used the SERVER cd of ubuntu 6.06.

Our problem starts with a step within the text-based partitionier:
We managed to make (software)raid-devices (md0 to md2) and they seem to okay (according to /proc/mdstats and they are synced). They are listed in the partitioner and we changed them from "do not use" to "use as LVM".
Now we wanted to "Configure LVM" and creating new LVGs, but this steps fails with an error message stating that the changes can't be communicated to the kernel.
In other words: we are not able to create any LVM-related things.

We found out that there is no modules loaded such as lvmcfg or alike and the command "modprobe lvmcfg" fails.

Did someone know what we might do or encountered the same problem and has a solution for us?

Thanks a lot for your help
Stefan

---

