---
title: "ipppd error"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by losersgiveup on 2010-01-17
I cant install or reinstall ipppd. the following error pops up.

The files device.ippp0 and ipppd.ippp0 already exist. Therefore the ipppd configuration phase won't touch anything there, as it looks like it's already been configured.

If it doesn't work yet, and you want to try the automatic configuration, stop all ISDN processes (use "/etc/init.d/isdnutils stop"), remove the files mentioned above, and rerun the configuration with "dpkg-reconfigure ipppd". After that, restart the ISDN processes: "/etc/init.d/isdnutils start".

---

