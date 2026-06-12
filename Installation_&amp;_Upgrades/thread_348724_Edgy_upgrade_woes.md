---
title: "Edgy upgrade woes"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by linuxpimp on 2007-01-29
Hi folks

First off, i upgraded my Thinkpad with zero effort and zero problems, well done to the Ubuntu team!

Now, my workstation is another story, some dependancy issues due to me installing drivers to try get XGL to work (never did :-) )

Please see these errors from /var/log/dist-upgrade/main.log
(i think these are the relevant lines.)
:
2007-01-28 21:43:05,414 DEBUG Installing 'hpijs' (hpijs quirk upgrade rule)
2007-01-28 21:43:05,494 INFO Forcing downgrade of libgl1-mesa-dri for xgl.compz.info installs
2007-01-28 21:43:05,585 DEBUG no {ubuntu,edubuntu,kubuntu}-desktop pkg installed
2007-01-28 21:43:05,585 DEBUG guessing 'ubuntu-desktop' as missing meta-pkg
2007-01-28 21:43:05,989 DEBUG The package 'nvidia-glx-dev' is marked for removal but it's in the removal blacklist
2007-01-28 21:43:38,639 ERROR Dist-upgrade failed: 'An essential package would have to be removed'


Please assist.

Thanks

lp

---

### Post by linuxpimp on 2007-01-29
Ok folks, i simply removed nvidia-glx-dev using Synaptic and the upgrade is in progress. Curious as to why the upgrade process did not do this itself?

Anyway, hopefully my next post will be post-upgrade.

LP

---

