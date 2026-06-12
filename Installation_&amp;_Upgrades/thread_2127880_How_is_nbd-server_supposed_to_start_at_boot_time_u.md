---
title: "How is nbd-server supposed to start at boot time under Ubuntu 12.04?"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by JoelAV on 2013-03-21
So, a client upgraded from 10.04 to 12.04 on a whim. Suddenly things didn't work. They have a couple old machines that they use as terminals with LTSP. After the upgrade they couldn't get the terminals to boot.

I've narrowed the problem down to the fact that nbd-server is not starting at boot time. I can start it manually with 'service start nbd-server' but since they are in the habit of shutting down the main computer that serves as the application server every night, they need it to come up automatically.

I've seen conflicting information about whether nbd-server is supposed to start with the old init, or with upstart in 12.04. There is an entry for nbd-server under /etc/init.d (old-style init, correct?) but that doesn't seem to start the server at boot time, and I don't see any sort of error message in /var/log/messages, or dmesg pertaining to nbd. There is nothing about nbd-server under /etc/init (upstart, no?) and 'initctl status nbd-server' says 'unknown job' or something like that.

So how is nbd-server supposed to start at boot time, and how does one get it to start if it isn't?

JCE

---

### Post by JoelAV on 2013-03-22
Am I asking in the wrong place?

JCE

---

