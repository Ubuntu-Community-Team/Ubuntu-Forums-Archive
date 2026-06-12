---
title: "Boot delayed on Ubuntu 18"
date: 2018-09-01
forum: Installation &amp; Upgrades
---

### Post by darkaht on 2018-09-01
Dear Sirs:

I tell you my problem, I hope you can help me:

I recently upgraded to ubuntu 18.04.1 and the startup is very slow.

I have a ssd disk and with ubuntu 16 I started very fast.

I have made the following checks:

- I have looked in / etc / fstab and there is no badly configured partition.

- dmesg -l err: does not throw any error

- systemd-analyze blame:

1.823s NetworkManager-wait-online.service

The process that takes more time is this, does not slow down the system.

systemd-analyze:

Startup finished in 19,827s (kernel) + 6,274s (userspace) = 26.101s

I have made the startup information visible and the problem does not seem to be that the start is late, the problem is that it takes time to start loading the kernel.

The screen stays black for a few seconds (more than 10 seconds) and then the system load begins.

The same problem occurs with kernels 4.15.0-29 and 4.15.0-33.

Any ideas?

---

