---
title: "Ubuntu 12.04 server on 3 HDD's"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by Marijn_Pool on 2013-10-20
Hello guys,

I am quite new to installing Linux. I have used it many many times in server environments but already installed and configured.
Now I want to set up my own Samba/Torrent/Web/Mail server and I fail miserably.

What I want:
Install ubuntu server in a safe way(Raid I guess) on 3 HDD's

Now I have tried multiple configurations with software raid and that just didn't work.
What I am hoping to get here:
A way to set up my system safely, so that when I lose a HDD I have lost no data and more importantly no config.

I hope you guys can help me to set up my system.

Marijn

---

### Post by TheFu on 2013-10-20
Use backups as the primary tool while you are learning.  RAID does not replace backups - EVER.

Sorry, but I've never used software RAID except for non-OS and non-boot partitions.  Real hardware RAID can be used  for the OS if the hardware is supported natively by Linux and if the RAID is not "fakeRAID" from a card or motherboard. In the old days, we didn't boot from RAID and there are still issues with this on Ubuntu. Some other distros appear to handle this better.

---

