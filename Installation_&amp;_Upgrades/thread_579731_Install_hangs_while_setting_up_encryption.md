---
title: "Install hangs while setting up encryption"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by tech0007 on 2007-10-18
hi! have a problem while installing gutsy. after the partition, install and cleanup part, restart, it brings up a blank screen w/ a bouncing Hz? box. when i go to console, i only see 'Setting up encryption on volume hda5_crypt....', it just hang there and its been there for 55! mins! i need help!

---

### Post by oremusnix on 2007-10-18
I assume you chose the alternate CD for installation and set i up to encrypt your hard disk.In that case this behaviour is normal as Ubunhtu is encrypting the partition before first use. This process takes a long time (last time with Debian 4.0 it took me around two hours on a 80GB HD).

Edit : Just installed 7.10 on my laptop. The encryption phase is not explicit like for Debian, some installation steps are a bit long and I suspect this is done behind the scene but all in all it took one hour on a pentium M 2Ghz, 80GB HD. Worked just fine.

I came back from Debian 4.0 and am now a proud ubuntu user again!

---

