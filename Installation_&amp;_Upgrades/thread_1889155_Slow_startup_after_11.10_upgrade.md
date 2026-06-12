---
title: "Slow startup after 11.10 upgrade"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by jbsterritt on 2011-11-30
Slow startup after installing 11.10 on Toshiba Satelite. Noticed long delay at tail of Syslog:
between 19:43:50 and 19:48:44.
**Nov 30 19:43:50 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1**
Nov 30 19:47:16 ubuntu anacron[951]: Job `cron.daily' started
Nov 30 19:47:16 ubuntu anacron[1827]: Updated timestamp for job `cron.daily' to 2011-11-30
Nov 30 19:47:16 ubuntu kernel: [  333.716060] CE: hpet increased min_delta_ns to 20113 nsec
[B]Nov 30 19:48:44 ubuntu AptDaemon: INFO: Quitting due to inactivity
Nov 30 19:48:44 ubuntu AptDaemon: INFO: Quitting was requested[/B]

---

### Post by creator101 on 2011-11-30
Sometimes opening the GRUB (holding shift at startup if you don't know) and selecting a kernel just one revision below the default speeds things up a lot while still using the same version of Ubuntu. so instead of using xx.xx.14, use xx.xx.13.

Hope that helps.

---

### Post by jbsterritt on 2011-11-30
Thanks, I'm new to Ubuntu so not too familiar with your instruction. I tried to hold down shift after starting the OS. It didn't do anything I could notice. I didn't see anywhere I could select a different kernel. If you get a chance, could you dummy-it down a little for me ? :)

---

