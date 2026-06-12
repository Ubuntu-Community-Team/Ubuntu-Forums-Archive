---
title: "Boot failure after upgrading 10.04 kernel from 2.6.32-22.35 to 2.6.32-22.36"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by torrya01 on 2010-06-04
I applied this update today to a couple of different servers (Dell Poweredge R410, Poweredge R710 and HP Proliant DL360 G6). Afterwards, none of them will boot successfully even after a total shutdown and restart.

I get the following message on the console:-

fsck from util-linux-ng 2.17.2
/sbin/fsck.xfs: XFS filesystem
boot: clean, 210/121440 files, 51031/242688 blocks
init: ureadahead-other main process (454) terminated with status 4

All kernels from the original 10.04 release up to and including 2.6.32-22.35 have worked fine on this hardware. I need the specific bugfix that 2.6.32-22.36 claims to provide. Anyone have any advice, solution or workarounds to this?

---

### Post by torrya01 on 2010-06-23
[SOLVED] In case it helps, it turns out that the machine IS actually booting. It can be reached over the network (ssh) and all services have started. It's just the console that gives the impression that the boot has failed, being stuck at the message described in the original post, and with the GUI login screen failing to appear. This behavior is also inconsistent - sometimes the machine boots to the GUI login screen, sometimes it appears to stop as described.

---

