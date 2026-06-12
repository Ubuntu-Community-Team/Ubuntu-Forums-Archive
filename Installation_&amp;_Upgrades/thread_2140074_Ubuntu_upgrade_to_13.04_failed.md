---
title: "Ubuntu upgrade to 13.04 failed"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by g00glen00b on 2013-04-28
Hi,

Today I upgraded to Ubuntu 13.04 (desktop environment x64) from 12.10 but in the middle of installation my system froze. I waited several hours but nothing happened so I had to do something which I rather not like to do, I had to use a hard shutdown.

While starting up everything seemed to work fine (13.04 logo and stuff) but when I tried to log in it would give me a black screen and redirect me to the login screen again.
So I tried shutting down the system again and starting it up, but at shut down I noticed that it took very, very long (minutes) and when I started up it said that the ELF header was smaller than expected.
I made a live USB with Ubuntu 13.04 on it and used boot-repair and tried to repair everything. The error is gone now, but now it says that it cannot find my operating system. I thought that maybe I could repair my Ubuntu 13.04 installation with the same CD, but because no operating system is found, it is not offering me an option to upgrade (only to overwrite everything).

When I look at the [logfile]("http://paste.ubuntu.com/5613074/") it created I notice that at none of the partitions has an operating system so I assume that there is a problem.

What is the best solution I can do now? Backup my old files and make a clean installation? Or can I somehow re-configure my bootloader so that it would find my messed up Ubuntu (and try to work out those problems)?

---

### Post by salil2 on 2013-08-20
hi,

Did you solve this issue? I'm facing now the problem of ELF header error, and even Boot-repair could not rectify it...

---

