---
title: "Howto: Updating XServer without fear"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by lptr on 2008-01-22
Hi there,

we all having had some troubles with updating for some times. Myself I am very concerned when the updater tells me, that kernel or - as in this case - xserver must be updated. The later especially because this machine also has VMware workstation installed providing me a quite complex testing field. So this machine MUST run. Yes and I am using the proprietary drivers from NVIDIA.

As usually I do wait some days for the update. If things seem ok I do following steps:
(could be that it is named differently as I having non english version running here)

```
Opening system settings
choosing advanced tab, limited drivers
deactivate NVIDIA drivers
reboot machine to kick drivers out of memory
on console
 sudo aptitude update
 sudo aptitude upgrade
restart system to get new X up and running
reactivate NVIDIA drivers
restart to get NVIDIA back into memory
as last step call config script from vmware
/usr/bin/vmware-config.pl
when script asks questions choose defaults
```After this steps you having an updated environment again.

Oh! This should work for ATI drivers, too.

rob*

---

