---
title: "An upgrade error - nscd &amp; octopussy"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by wmtmanjula on 2008-11-11
Hi All 

I have a upgraded Ubuntu server from 7.10 to 8.04 recently. When I tried to upgrade this version with apt-get update the following error occurred.
I tried with apt-get -f install and upgrade again but still the same.

anyone has an idea?

Thanks!
Manjula

dpkg: dependency problems prevent configuration of octopussy:
 octopussy depends on nscd; however:
  Package nscd is not configured yet.
dpkg: error processing octopussy (--configure):
 dependency problems - leaving unconfigured
Setting up logrotate (3.7.1-3ubuntu0.8.04) ...
Setting up python-apt (0.7.4ubuntu7.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nscd
 octopussy
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wmtmanjula on 2008-11-30
Cool..!
i could solve this problem just by stopping the nscd service 

 pgrep nscd (find pid kill - not necessary)

/etc/init.d/squid stop

sudo apt-get update

sudo apt-get upgrade

cheers..!
Manjula

---

### Post by wmtmanjula on 2008-11-30
:)

---

