---
title: "Automatic upgrade from 19.10 to 20.04 fails"
date: 2020-05-08
forum: Installation &amp; Upgrades
---

### Post by Hasimir on 2020-05-08
Hi,

I'm running Ubuntu 19.10 and today the system notified me that the OS could be upgraded to 20.04.
But when I click YES the software upgrade window closes and ... nothing.
Nothing happens.
I tried to start the process from command line, but it just says the software is up to date.

How can I fix this?

---

### Post by Hasimir on 2020-05-08
The command
[B]do-release-upgrade -d

[/B]return the following error:
**Upgrades to the development release are only available from the latest supported release.**

**lsb_release -a** tells me that:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.10
Release:	19.10
Codename:	eoan

---

### Post by mörgæs on 2020-05-08
There are only minor differences between 19.10 and 20.04 so if 19.10 is working fine you could keep it until july.

Anyway, if you want 20.04 then a clean install is a safer approach than trying to upgrade.

---

