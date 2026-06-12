---
title: "Remote upgrade of packages"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by renzo2000 on 2006-11-21
Hi all,

I've been searching the web now for 1 week, looking for at solution to my problem -- how to manage large Ubuntu 6.06 LTS Server farms. ](*,) 

The problem:
I want to be able to manage the upgrading of packages from a single interface (eg. web based). From there i shall be able to see a list of my servers with a indication of there is any upgrades available (red/yellow/green). 

If a choose to upgrade a server, i shall support to upgrade individual packages, not a whole dist-upgrade. In live production environments maybe some packages cannot be installed due to conflict with the application the server is running, and again some does not.

The centralized tool shall then direct the "proxy" on the server to contact the upgrade server to perform an upgrade.

I don't want to build another package management tool, there is plenty out there, but i cannot believe i am the only with this problem.

I looked at the following to find a solution: 
apt-get, smart, dkpg, Conary, lpmtool. 

with no luck. 

Any help / suggestions is very, very appreciated! 

Regards
Søren Michael Nielsen

---

