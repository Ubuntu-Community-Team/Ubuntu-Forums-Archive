---
title: "dpkg --configure -a  fails"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2008-11-06
root@ramaswamy-desktop:~# dpkg --configure -a
dpkg: status database area is locked by another process
root@ramaswamy-desktop:~# dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
root@ramaswamy-desktop:~#


this is caused by synaptic getting stuck and froze the system.
i was installing xorg-driver-fglrx.
and power failure is common here.

here is the report from apt

root@ramaswamy-desktop:~# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing xorg-driver-fglrx (--configure):
 package xorg-driver-fglrx is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
root@ramaswamy-desktop:~#

this new ubuntu-8.10 behaves worse than windows98 in getting stuck frequently.

what is out from this?

other hand it works fine in laptop with all desktop effects of kde4

only 845 mobo p4 desktop it gives lot of troubles.
except vesa nothing works for screen driver.:(

---

### Post by frankleeee on 2008-11-06
You have to have sudo in front of the command sudo dpkg --configure -a
Also don't run it in root but the regular terminal with everything else off

---

