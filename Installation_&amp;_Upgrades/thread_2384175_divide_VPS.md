---
title: "divide VPS"
date: 2018-02-03
forum: Installation &amp; Upgrades
---

### Post by w-gu2do-0 on 2018-02-03
[COLOR=#333333][FONT=Ubuntu]I want to divide my VPS (3 TB) into 2 partitions of 1.5 TB. Partition 2 should be used for backup.
The VPS is an empty one.
I am using the fdisk command.
After partitioning and writing to the disk, I am unable to boot my VPS.

I did the following:
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]
# fdisk /dev/sda[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Command: d[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Partition: 3[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Command: n[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Partition: 3[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]First sector: Enter[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Last sector: 3075274735[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Command: n[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Partition: 4[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]First sector: Enter[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Last sector: Enter[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Command: w[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]# reboot[/FONT][/COLOR]

My VPS doesn't boot. It doesn't ask me to login.
In my control panel I reconfigured the VPS and started over again.
[COLOR=#333333][FONT=Ubuntu]The VPS doesn't ask me to login. Via the control panel of the VPS I reconfigured the VPS.

Which command do I have to give after the above mentioned commands?
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]
Kind regards,
Guido

[/FONT][/COLOR]

---

