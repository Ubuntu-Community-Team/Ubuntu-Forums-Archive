---
title: "Problem updating from 10.4"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by msanchez3 on 2011-11-15
Hi!

I'm trying to update form 10.4 to the latest release and I have this errors:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                         
  404  Not Found

W: No s'ha pogut obtenir [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found




Maybe this helps...:


cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
marcel@PCETS18:~$ 



Thank you!

---

### Post by zvacet on 2011-11-15
You can not skip versions and upgrade directly from 10.04 to 11.10.You will have to do 

10.04>10.10>11.04>11.10

I think it is lot of work and downloads with no guaranty it wil end up O.K.You have two options

1. store all your valuable data somewhere else ( external hd or similar) and do fresh install of 11.10

2. you can upgrade from one LTS to another so when 12.04 is released you will have option to do it.

Before any upgrade remove ( or uncheck) all third party and PPA sources from source list.

---

### Post by raja.genupula on 2011-11-15
> **zvacet said:**
> You can not skip versions and upgrade directly from 10.04 to 11.10.You will have to do 

10.04>10.10>11.04>11.10

I think it is lot of work and downloads with no guaranty it wil end up O.K.You have two options

1. store all your valuable data somewhere else ( external hd or similar) and do fresh install of 11.10

2. you can upgrade from one LTS to another so when 12.04 is released you will have option to do it.

Before any upgrade remove ( or uncheck) all third party and PPA sources from source list.

+1 i agree with him .
while coming to your issue sometimes change your ubuntu server to other mirror solve the issue.
update manager -> settings -> 1st tab ->download from ...
change from there and try again

---

