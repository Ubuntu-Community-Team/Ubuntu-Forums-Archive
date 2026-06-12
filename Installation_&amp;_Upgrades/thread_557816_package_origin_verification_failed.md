---
title: "package origin verification failed"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by psyberd on 2007-09-23
I seem to have a problem with my apt signatures, possibly my apt keyring. When trying to install packages through Synaptic, apt-get or dpkg, installation of ALL packages fail due to verification. Using --force-bad-verify in the cache works... but I'd rather fix it.
The keys show up in apt-key and in Synaptic options, and there's no problem with repository authentication on getting the package. My loose guess is there's some problem with access permissions or locking of the apt keyring interfering with verification of the packages.
No other manager programs are running. I've tried using apt-get clean and apt-get install -f and ive tried packages from both Ubuntu itself and 3rd party and the problem is persistent. I've searched here and googled it and find no fix.

Ubuntu FF 7.04 running in VMware workstation 6 on XP - 20gb container, 512mb ram allocated, VM tools installed.

Any help appreciated.

---

