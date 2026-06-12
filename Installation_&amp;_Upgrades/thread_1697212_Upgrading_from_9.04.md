---
title: "Upgrading from 9.04"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by SalishSea on 2011-02-28
I need to upgrade a machine from 9.04. (I know I know... long story). I gather the path is 9.04 to 9.10 to 10.04 or 10.10. 

Currently the apt-get command tries to link to:
 mirror.lcsee.wvu.edu (157.182.36.117)

which no longer appears to be working.  I presume there must be a repo that can support 9.04 long enough to sustain the dist-upgrade, nest pas?


I'd welcome suggestions.

---

### Post by smurphy_it on 2011-02-28
I doubt it.  The support period has ended.  Your course of action would be a "fresh install".

Version 	Code name 	Release date 	Supported until
                                                Desktop 	Server
9.04 	Jaunty Jackalope 	2009-04-23 	2010-10-23

Taken from:  [http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29)

---

### Post by coffeecat on 2011-02-28
> **SalishSea said:**
> I presume there must be a repo that can support 9.04 long enough to sustain the dist-upgrade, nest pas?

Indeed there is. You'll need to use the old-releases repo to go from Jaunty to Karmic. Have a look here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Which has a link to this page:

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

Good luck with that.

---

