---
title: "Upgrade to 7.04 failed ... need to restore"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by jdogzilla on 2007-04-04
Hello all, my upgrade to fiesty 7.04 failed.  There was a message in the end about dpkg, but all the windows just closed.  Is there any way that I can restore my environment back to edgy 6.10?  What do I need to do - update the sources.list file?  What app/command can I run to restore?  Please help !!!

---

### Post by maheshjagadeesan on 2007-04-04
> **jdogzilla said:**
> Hello all, my upgrade to fiesty 7.04 failed.  There was a message in the end about dpkg, but all the windows just closed.  Is there any way that I can restore my environment back to edgy 6.10?  What do I need to do - update the sources.list file?  What app/command can I run to restore?  Please help !!!
Two ways to go about this:
a. when your system boots, you can simply select the previous kernel version
b. during the boot, select "recovery mode" from the grub menu and run the upgrade from the console. This should help you hunt for errors and either resolve them yourself, or post specific errors to the forum.

---

