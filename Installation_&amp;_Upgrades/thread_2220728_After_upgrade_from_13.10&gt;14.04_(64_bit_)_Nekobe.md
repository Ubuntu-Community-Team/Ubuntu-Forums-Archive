---
title: "After upgrade from 13.10&gt;14.04 (64 bit ) Nekobee won't startup as a stand alone"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by winko2 on 2014-04-29
After upgrading 4 machines of the 64 bit 13.10 > 14.04, Nekobee won't startup as a stand alone instrument anymore. Nekobee works when started from Qtractor. When trying to start from the command line, I get “jack-dssi-host: Warning: DSSI path not set”, “jack-dssi-host: Defaulting to "/usr/local/lib/dssi:/usr/lib/dssi:/home/<username>/.dssi" ” and “ jack-dssi-host: Error: Failed to load plugin library "nekobee.so" ”.  

The work around is editing the file /usr/bin/nekobee and change its content to jack-dssi-host /usr/lib/x86_64-linux-gnu/dssi/nekobee.so

Regards,

Winko

---

