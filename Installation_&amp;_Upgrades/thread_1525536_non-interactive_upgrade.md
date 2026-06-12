---
title: "non-interactive upgrade?"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by e-a-c on 2010-07-06
Is it possible to do an non-interactive upgrade? I need to upgrade to 10.04 and I would like to just have it accept all of the default selections (remove obsolete packages, replace custom configs, etc), and just log it all somewhere so I can double check it later, instead of prompting me every half hour. I don't have time to sit in front of my computer for 3 hours just waiting to click "OK" but I would really like to upgrade.

I tried looking at documentation for do-release-upgrade but it's pretty sparse; maybe the "--frontend" option could help me? I can't find any documentation on what frontends are available though.

---

### Post by bhy on 2011-08-25
I found these two things:

[http://penguinpython.com/blog/2011/05/upgrading-ubuntu-rackspace/](http://penguinpython.com/blog/2011/05/upgrading-ubuntu-rackspace/)

[https://wiki.ubuntu.com/FoundationsTeam/Specs/KarmicLandscapeReleaseUpgrades](https://wiki.ubuntu.com/FoundationsTeam/Specs/KarmicLandscapeReleaseUpgrades)

I'm not exactly sure whether the second thing is supposed to do what we want, but if so, it makes the first thing a bit of an overkill.

I haven't tested either so far. I'll be back to report the results.

---

### Post by hnghng on 2011-12-13
We had to do a non-interactive ubuntu release upgrade on our project environment on multiple machines. It was from ubuntu 11.04 to 11.10 and we used DEBIAN_FRONTEND=noninteractive with apt-get dist-upgrade and some force-yes options. You just have to change your sources.list to match the new release. Here's our [blog post]("http://awaseconfigurations.wordpress.com/2011/11/21/automated-ubuntu-release-upgrade/") about it.

---

