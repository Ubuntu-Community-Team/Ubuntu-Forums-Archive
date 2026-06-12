---
title: "Install 2 MySQL Servers on Ubuntu Server"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by 1pirredabbe on 2016-10-15
Okay so I have a VPS with Ubuntu Server 15.10 x64 that is rocking 50GB RAM, 10Core CPU, 1Gbps network link, 1.2TB SSD and some other cool stuff.

I have 2 IPs on the machine and both are assigned to it.

I have a MySQL server installed and running on the main IP adress, but can I install a second MySQL server that runs on the second IP without doing virtual machines (that is also not possible since it's a VPS already)?

Me and my friend are making a Gaming Community on it, but rather than just using the same MySQL server and use the 2nd IP for "my" gameservers, we want to use a secondary MySQL server for my projects.

Is this possible?

Rememer that it's Ubuntu Server with terminal-only access.

---

### Post by QIII on 2016-10-15
Hello!

Just poking my head in to say that 15.10 has passed its End Of Life (EOL) and is no longer supported.  That means that it is not getting any security updates.  If it is exposed to the web, it is vulnerable.

You may want to update to a supported version before you even consider anything else.

Cheers!

---

