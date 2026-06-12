---
title: "Force aptitude to use a new version than the distro prescribes"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by mschipperheyn on 2011-01-03
Hi,

I use Lucid Lynx and I want to use a newer version of nginx (8+) than the one that the distro provides (7+).

I've been trying to find a way to do this with aptitude but haven't really found anything that doesn't involve manally installing the software or upgrading the distro, both of which I would like to avoid.

Is there any way to do this?

Cheers,

Marc

---

### Post by dino99 on 2011-01-03
open synaptic repo tab (third party) and add this ppa:

[https://launchpad.net/~brianmercer/+archive/nginx](https://launchpad.net/~brianmercer/+archive/nginx)

then update, upgrade

or one of those:
[https://launchpad.net/ubuntu/+ppas?name_filter=nginx](https://launchpad.net/ubuntu/+ppas?name_filter=nginx)

---

