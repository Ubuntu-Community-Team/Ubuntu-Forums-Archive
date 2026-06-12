---
title: "Upgraded 9.04 to 9.10: Wireless Stopped Working"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Conzar on 2009-11-23
I previously had installed 9.04 netbook remix on an OCZ Neutrino netbook.  Everything worked without any problems on 9.04.  Today I upgraded to 9.10.  After the upgrade, the wireless stopped working.

/var/log/messages reports the Linux kernel driver for RTL8180 / RTL8185 is being loaded.  I am able to search for available networks; however, I am unable to connect to the available networks.  

Any ideas what might be wrong?

Thanks

---

### Post by Conzar on 2009-11-24
Today I formatted and installed 9.10 cleanly.  After doing this I still cannot connect to a wireless network.

After looking the in the log file, I see many warning about:
"WARNING: at /build/buildd/linux-2.6.31/net/core/dev.c:2025 net_tx_action+0x128/0x130()"

This is right after a message about "linking with <network name>: channel is 10"

Any ideas?

---

### Post by Conzar on 2009-11-24
Just re-installed 9.04 and the wireless is working again.  Looks like I won't be using 9.10 until this issue gets fixed.

---

