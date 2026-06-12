---
title: "Ignored repositories when updating package list"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by lucacerone on 2010-12-03
Dear all,
I'm experiencing a strange issue with my Ubuntu 10.10 since a few days:
when trying to update the packages list, a lot of repositories are ignored.

Here is the output of ```
 sudo apt-get update | grep -i ign 
```.
> 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_GB
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/txwikinger/php5.2/ubuntu/](http://ppa.launchpad.net/txwikinger/php5.2/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/txwikinger/php5.2/ubuntu/](http://ppa.launchpad.net/txwikinger/php5.2/ubuntu/) maverick/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_GB
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_GB
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_GB
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_GB

How come all these repositories cannot be hit?

Is there any way to make the update hit there repositories?
And if they're useless, no longer supported, how can I remove them
so to have a tidy repositories list?

Thanks a lot in advance to all of you,
Cheers, -Luca

---

### Post by zvacet on 2010-12-03
I tried your repos and they work for me ( i can go to the web page).All you miss is translation packages.So you can live without them for few days.I hope in that time frame your problems will disappear.

---

### Post by lucacerone on 2010-12-08
Thanks,
Cheers, -Luca

---

### Post by Earl_Maroon on 2010-12-15
I too am getting fails on these when I reload in synaptic.

---

