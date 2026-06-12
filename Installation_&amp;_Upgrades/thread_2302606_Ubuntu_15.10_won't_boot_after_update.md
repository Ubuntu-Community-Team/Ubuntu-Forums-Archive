---
title: "Ubuntu 15.10 won't boot after update"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by coconutdog2 on 2015-11-11
My system upgraded from 14.10 to 15.10 without any problems and was working well. It then did a kernel upgrade and then a wps upgrade (I think?) and now it won't boot to the GUI. The GUI logon screen briefly shows and the goes back to the text based boot up screen. It stops at the point where it says, "[OK] Started Light Display Manager" and freeezes. Any ideas on how to fix this? I have restarted into Linux 4.2.0-18-generic recovery mode and run dpkg which didn't help. Restarting to an earlier kernel also doesn't fix the problem. Any ideas? Matt.

---

### Post by xsnake_ on 2015-11-11
I would first try to rule out any issue with the GPU drivers, can you try to initiate the system on perhaps an Integrated Graphics Device, or trying to blacklist any kernel modules associated with your GPU?

---

