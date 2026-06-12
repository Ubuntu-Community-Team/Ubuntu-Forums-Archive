---
title: "Upgraded to 8.10, hangs on 'Configuring Networking..;"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by dammad on 2008-11-14
I had 8.04 server and upgraded to 8.10 server recently (both 64bit AMD). The old 8.04 worked great, and the new 8.10 works fine too, except at bootup and shutdown. 

During either bootup or shutdown, the boot hangs at the networking part ("Configuring Network... [OK]" on boot) until you press Enter. After pressing Enter it is all fine. 

Running ifup and ifdown after the boot work seamlessly, so its a bit weird to have it waiting for ENTER on boot. I'm using this on a server, so waiting for ENTER is a real pain. If I can't fix it, I'm gonna have to downgrade to 8.04 server again.

What gives? Anyone else seen this?

---

### Post by dammad on 2008-11-16
Bump.

---

### Post by hellblade on 2008-11-19
I have the same problem using Kubuntu 8.10 upgraded from 8.04.

My setup has a single wired 100mb interface with static configuration. Uninstalling network manager didn't help.

---

### Post by dammad on 2008-11-19
Glad to hear I'm not alone, but alas we have no fix. It is wierd that 'ENTER' fixes the problem. No other key seems to allow it to continue.

---

