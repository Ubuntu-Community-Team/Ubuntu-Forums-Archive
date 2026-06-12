---
title: "KDE4.3 refuses to reboot/shutdown/hibernate (karmic)"
date: 2009-07-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by A_Modest_Proposal on 2009-07-18
as mentioned in my title my kubuntu 9.10 installation recently started refusing to perform any type of power down function without prefixing kdesu/sudo.
the odd thing is it seems all my policykit permissions are in place and hal/dbus responds to:
```
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot
```
with the expected result of a reboot when typed into konsole.

even worse this problem doesnt seem to affect my laptop which has gone though all the same updates.

im getting really tired of trying to troubleshoot this myself as i receive no feedback from the gui when clicking the shutdown button. instead kde seems to function as normal with the exception of not allowing me to bring up the "leave" menu again.

i have a few ideas but i dont have enough knowledge of kde4 to test them.
if anyone out there has any enlightening suggestions i would be thrilled to hear them.



*never mind. laptop now displays same problem. working on bug report.

---

### Post by Landrovan on 2009-07-26
I got the same problem. If you create a bug, can you give us a ticket number and if you post it on the kde bug tracking or on launchpad.

If you found a solution can you give it please?

Thanks

P.S. I use kubuntu jaunty (9.04) with kde4.3rc3

---

