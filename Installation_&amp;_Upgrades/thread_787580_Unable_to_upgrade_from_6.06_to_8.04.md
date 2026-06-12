---
title: "Unable to upgrade from 6.06 to 8.04"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by lonetree on 2008-05-09
Hi guys,

hope someone can help me on this. I recently tried to upgrade my ubuntu 6.06LTS to 8.04, however, I think I have screwed up upgrade process in the desktop environment, after which I am left with my text mode, all services are still running as per normal, and when I checked the version, it returns as follow:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper

X is no longer available and gdm was removed automatically.

when I tried to do a apt-get update, it updated but an apt-get upgrade returns the following error:

----------- begin --------
dpkg: dependency problems prevent configuration of apt:
 dpkg (1.14.16.6ubuntu3) breaks apt (<< 0.7.6ubuntu6) and is installed.
  Version of apt to be configured is 0.6.43.3ubuntu3.
dpkg: error processing apt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

--------- end ----

I am lost now. Does anyone has a solution to resolve this?

thanks in advance

regards,

---

