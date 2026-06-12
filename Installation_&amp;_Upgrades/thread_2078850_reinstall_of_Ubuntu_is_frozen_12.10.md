---
title: "reinstall of Ubuntu is frozen 12.10"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by buckyball60 on 2012-10-31
Hello, I am re-installing ubuntu from a liveUSB (keeping the same '/home' rewriting '/').
The install program has looped at the 'Running post-installation trigger update-notifier-common' point.  At this point I am just leaving it looping.  It should be noted that my wireless driver has never been natively supported and I have always needed to run it through ndiswrapper. At the start of the install it asked me to unmount my HDD, I could get you the exact driver/card if it would be ok to either kill this install OR safely mount my HDD at this point. 
This is a windows dual boot, but that was months ago, this isnt the first dual boot install (in fact windows was installed second, a pain in the rear).
Output from install GUI:

```
Oct 31 16:07:53 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:07:53 ubuntu kernel: [ 4099.386213] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:08:21 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:08:21 ubuntu kernel: [ 4126.646467] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:08:23 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:08:23 ubuntu kernel: [ 4128.651097] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:09:20 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:09:20 ubuntu kernel: [ 4186.204125] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:09:22 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:09:22 ubuntu kernel: [ 4188.166833] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:11:19 ubuntu kernel: [ 4305.371900] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:11:19 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:11:21 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:11:21 ubuntu kernel: [ 4307.305292] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:11:50 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:11:50 ubuntu kernel: [ 4336.000033] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:11:52 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:11:52 ubuntu kernel: [ 4337.922971] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:12:21 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:12:21 ubuntu kernel: [ 4367.102869] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:12:23 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:12:23 ubuntu kernel: [ 4368.991528] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:12:53 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:12:53 ubuntu kernel: [ 4398.682382] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:12:54 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:12:54 ubuntu kernel: [ 4400.626302] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:14:30 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:14:30 ubuntu kernel: [ 4496.438763] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:14:32 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:14:32 ubuntu kernel: [ 4498.340739] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:15:05 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:15:05 ubuntu kernel: [ 4531.449848] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:15:07 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:15:07 ubuntu kernel: [ 4533.435728] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:15:40 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:15:40 ubuntu kernel: [ 4566.607730] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:15:42 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:15:42 ubuntu kernel: [ 4568.520234] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:16:14 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:16:14 ubuntu kernel: [ 4600.192787] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:16:16 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:16:16 ubuntu kernel: [ 4602.115796] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:17:01 ubuntu CRON[25046]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 16:17:53 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:17:53 ubuntu kernel: [ 4699.082085] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:17:55 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:17:55 ubuntu kernel: [ 4701.004608] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:20:28 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:20:28 ubuntu kernel: [ 4854.046882] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:20:30 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:20:30 ubuntu kernel: [ 4855.938455] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:23:00 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:23:00 ubuntu kernel: [ 5006.579535] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:23:02 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:23:02 ubuntu kernel: [ 5008.607435] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:23:30 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:23:30 ubuntu kernel: [ 5035.781673] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:23:32 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:23:32 ubuntu kernel: [ 5037.715201] r8169 0000:04:00.0: >eth0: link up
Oct 31 16:24:29 ubuntu NetworkManager[3039]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 31 16:24:29 ubuntu kernel: [ 5095.161077] r8169 0000:04:00.0: >eth0: link down
Oct 31 16:24:31 ubuntu NetworkManager[3039]: <info> (eth0): carrier now ON (device state 100)
Oct 31 16:24:31 ubuntu kernel: [ 5097.325303] r8169 0000:04:00.0: >eth0: link up
```

---

### Post by buckyball60 on 2012-10-31
One extra note: 

This is my second re-install attempt today.  The first one worked flawlessly (I think) and the only difference is, I didn't check the 'install third party programs' radio button on the first install.  Unfortunately I also did not tell the first install attempt that sda1 was supposed to be the /boot which meant the MBR wasnt where it should have been hence this second install.

---

