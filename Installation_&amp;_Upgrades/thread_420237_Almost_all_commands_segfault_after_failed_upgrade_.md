---
title: "Almost all commands segfault after failed upgrade from Edgy to Feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by siennalizard on 2007-04-23
Dear all,

Unlike the last upgrade I did (to Edgy from Dapper) where I changed the sources.list in the unapproved manner and did a dist-upgrade, I decided to follow the rules this time. I dutifully clicked the upgrade distribution button in Update Manager and let it get on with a proper upgrade. Things seemed to be going well: all the packages were fetched, then I ran out of disk space. I was informed of this and freed up the necessary space before running Update Manager again.

This time, though, it died after a while with a segfault. Gradually, I discovered that everything seemed to be segfaulting, and the system now will not boot.

To try to save my system, I booted with the live CD, chrooted on to my drive, but everything continues to segfault, preventing me from mending the installation with the usual tools.

I suspect a major library is corrupt, but does anyone know the details and how I might get out of this mess without reinistalling?

Many thanks,
J.

---

