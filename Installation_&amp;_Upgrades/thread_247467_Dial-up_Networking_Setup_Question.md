---
title: "Dial-up Networking Setup Question"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by jsquared on 2006-08-30
I installed Dapper (6.0.6) ... and used pppconfig to configure dial-up networking ... it works fine if I use "pon" and "poff" from a terminal window after the system is booted.

But during the boot, I hear the modem being dialed, and use of the "plog" after boot (before running "pon" manually) shows that a network connection was attempted, and failed to PAP authentication issues.

So where is the attempt coming from during startup, and how can I examine the configuration files for this process (which is apparently separate enough from "pppd/pon" so that it is getting its username and password from some other file(s) than "/etc/ppp/peers/provider"?

I'm pretty confused about how "wvdial" and "pppconfig" operate, and whether there is another setup beyond these two ... ???  Any help understanding the boot process and what is running the connection attempt during startup will be appreciated!

-- Joe

---

