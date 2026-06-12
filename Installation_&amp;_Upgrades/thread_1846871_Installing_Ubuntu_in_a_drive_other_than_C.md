---
title: "Installing Ubuntu in a drive other than C"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by pandabiren on 2011-09-19
I tried to install Ubuntu through Oracle Virtual Box in a drive F The operating system (Win 7) is in drive C of course.When I installed it the relevant files failed to appear in drive F though Ubuntu appeared to be running normally. When I installed Guest Utilis Ubuntu failed to reboot; I had to remove Ubuntu ultimately. It is not possible to install in drive C because of memory constraints I would be very thankful if any forum member helps me in overcoming this problem.

---

### Post by mikewhatever on 2011-09-19
VirtualBox installations are done in virtual disks (created during the virtual machine setup), which can be on any Windows partition. That said, they are usually not in memory, so that memory constrains seem irrelevant.

---

