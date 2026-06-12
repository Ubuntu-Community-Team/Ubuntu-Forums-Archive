---
title: "Open-ISCSI Connection very slow after upgrade to Ubuntu 20.04"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by vmsman on 2020-04-25
I have upgraded four systems to 20.04 so far.  All have performed very well with the exception of my main system.  After diagnosing the problem with:

$ systemd-analyze blame

I discovered that my open-iscsi startup is taking 2 minutes 50 seconds.  This used to take about 8 seconds prior to the upgrade.  In addition, after the system is booted and I login, my ethernet device shows online 
but it is not.  I have to take it offline and back on and then everything is fine.  The interesting thing is that the iscsi initiator is connecting to and accessing the target just fine and the drive is properly 
mounted in the fstab.

I deinstalled open-iscsi on this system and it boots very quickly now and there are no issues with the ethernet device connecting all the time.  My open-iscsi package and all its dependencies were completely up to
date.  Has anyone seen this happen?

---

