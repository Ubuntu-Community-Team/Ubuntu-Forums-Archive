---
title: "computer wont install or upgrade"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by philipballew on 2010-11-20
when i try to open the software center it does nothing and just wont open. when i open the synaptic software center i get this error 

E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/lucid-bleed-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

when i open update manager i the progress bar goes about two-thirds of the way across and then this error arrives.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/lucid-bleed-ppa-maverick.list'
 how can i fix this?

---

### Post by kansasnoob on 2010-11-20
You need to remove or disable the "-bleed" ppa.

It's obviously NOT well maintained.

---

### Post by sikander3786 on 2010-11-21
> **kansasnoob said:**
> You need to remove or disable the "-bleed" ppa.

It's obviously NOT well maintained.
Go to Software Center > Edit Software Sources > Other Software Tab for that.

Or it might just be a syntax problem in there. You can try adding it back again after disabling and it might really help.

---

