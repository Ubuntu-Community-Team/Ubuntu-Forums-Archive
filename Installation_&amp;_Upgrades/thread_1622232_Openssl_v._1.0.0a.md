---
title: "Openssl v. 1.0.0a"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by panos-gr on 2010-11-15
Hello,

   Does anyone know when ubuntu will offer openssl v.1.0.0a package in its repository? Openssl 1.0.0 has been released for more than six months and it would be very good to be able to get it from the repository and avoid building it manually and having to recompile all the programs that depend on it...

   Thanks a lot!

---

### Post by dino99 on 2010-11-15
Thanks for pointing this outdated package, ive opened a report, suscribe to it.

[https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/675566](https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/675566)

---

### Post by panos-gr on 2010-11-15
Many many thanks! that is very useful indeed! I will certainly subscribe!

would the report be for the latest version of ubuntu only? 10.10? what about 10.04?

---

### Post by dino99 on 2010-11-15
ive search deb package and rpm too, but cant find any more recenent than ours. Even they build for the latest (natty) its easy to use it on the other release/distro using dpkg -i anyway.

Hope that a dev build it soon :)

---

### Post by panos-gr on 2010-11-15
I hope so too, because there are indeed a lot of people looking for it, judging from interest in mailing lists...

---

### Post by panos-gr on 2010-11-15
by the way, fedora, opensuse and other distros have rpm of openssl 1.0.0a

e.g. 
[http://rpm.pbone.net/index.php3?stat=3&search=openssl&srodzaj=3](http://rpm.pbone.net/index.php3?stat=3&search=openssl&srodzaj=3)

---

### Post by dino99 on 2010-11-15
wow your search is better than mine :)

so lets go with alien

---

### Post by panos-gr on 2010-11-15
I would definitively want to avoid alien, because openssl is a very serious package. eg. if you try to remove it, there are 46 packets that depend on it (among those ubuntu-desktop) as well...

so i wouldn't like to risk alien messing up my system, because it can very easily end up with an unusable after removing openssl and trying to alien and dpkg the outcome of it...

what do you think?

---

