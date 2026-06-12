---
title: "Synaptic Package Manager error"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by cage27 on 2010-08-23
When I try open Synaptic Package Manager I get the following message.> E: Type ‘[http://mirror.oscc.org.my/medibuntu/’](http://mirror.oscc.org.my/medibuntu/’) is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


---

### Post by amauk on 2010-08-23
you've got an error in your package sources list

Open up System > Administration > Software Sources

On the "Other Software" tab, look for the offending entry, and disable it

---

