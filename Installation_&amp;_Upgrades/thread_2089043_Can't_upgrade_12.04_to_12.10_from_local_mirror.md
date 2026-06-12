---
title: "Can't upgrade 12.04 to 12.10 from local mirror"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by minhazr on 2012-11-28
Followed these steps for upgrading:
1. Updated the software list:
```
sudo apt-get update
```2. Upgraded current softwares (Just to be safe):
```
sudo apt-get upgrade
```3. Initialized the updater:
```
sudo update-manager -d
```After the updater gets necessary information I get this error on "Setting new software channels" stage:
> Invalid package information
After updating your package information, the essential package 'ubuntu-minimal' could not be located. This may be because you have no official mirrors listed in your software sources, or because of excessive load on the mirror you are using. See /etc/apt/sources.list for the current list of configured software sources.
In the case of an overloaded mirror, you may want to try the upgrade again later.Additional information:
1. I am using a local mirror, [http://mirror.dhakacom.com/](http://mirror.dhakacom.com/) since the official mirror, [http://bd.archive.ubuntu.com/](http://bd.archive.ubuntu.com/) (CNAME of mirror.ispros.com.bd) is dead.
2. I disabled all the PPA from Synaptic, that is what I did when upgrading to 12.04 from 10.04.

What might be the problem? Or is there something wrong in the procedure?

---

