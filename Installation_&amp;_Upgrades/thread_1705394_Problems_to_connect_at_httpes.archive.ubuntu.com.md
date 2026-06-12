---
title: "Problems to connect at http://es.archive.ubuntu.com"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by OsmosisJones on 2011-03-12
Hi,

I have a spanish version of Ubuntu 10.10 and when I try to update packets from Synaptic it freezes because it is trying to connect to a repository that no response ([http://es.archive.ubuntu.com/](http://es.archive.ubuntu.com/)).

If I connect directly, the only thing I have is a pretty "timeout error", meanwhile from [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) I have no problems.

My question is, Is there any problem to switch between "es" and "us" version (or another) into the source list if I have, in this case, a spanish version?

I have problems with this repositories:

```
http://es.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg
http://es.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-es.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-es.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-es.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-es.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-es.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-es.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-es.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2
http://es.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-es.bz2

```

Greetings.

PS: my apology for my english.

---

### Post by ~Plue on 2011-03-12
> **OsmosisJones said:**
> Hi,
My question is, Is there any problem to switch between "es" and "us" version (or another) into the source list if I have, in this case, a spanish version?

nope. since they are just [mirrors]("http://en.wikipedia.org/wiki/Mirror_%28computing%29"), you can switch to anyone you want.

usually, if you're having trouble with the mirror of your choice, switching to the 'Main server' would most likely help out (from synaptic > edit menu > repositories)

---

### Post by OsmosisJones on 2011-03-12
Thank you very much!

---

