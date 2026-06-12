---
title: "Ubuntu server 14.04 RAID 1 setup"
date: 2014-07-09
forum: Installation &amp; Upgrades
---

### Post by Victor_Cheung on 2014-07-09
I'm installing a new server in addition to old servers.

And 14.04 LTS when detecting drive stage, it prompts one more option mdadm configuration in addition to serial ATA RAID configuration.
No matter whether I choose yes->yes / yes->no / no->yes, after installing finishes and the computer restarts, the RAID 1 will show degraded (it's intel BIOS RAID.)

It didn't happen with 12.04 LTS, 12.04 doesn't prompt mdadm, but only prompt serial ATA RAID 1, apart from later you have to manually enter map/... after entering a shell for content install, everything works fine.

So what did I do wrong?

Thanks.

---

