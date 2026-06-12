---
title: "Server upgrade 10.04 LTS - 12.04 LTS stuck on &quot;Setting up keyboard-configuration&quot;"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by skipx on 2014-10-28
Basically I feel being in deep trouble since whatever I tried my server upgrade gets stuck in 
```
Setting up keyboard-configuration (1.70ubuntu5) ...
```
Install seemed alsmost done when suddenly this kicked in.

The server is in a datacenter. Has roughly 20 mysql-databases and like 30 users. I'm hoping not having to reinstall the whole thing :'( 
What would be the solution? Would it be enough to go to the datacenter and attach a keyboard? :p Or is there a way arround I didn't found yet?
I did have several hours (like 5) on google on this but did not found a lot at all.. 

I did kill the install but "dpkg --confiugre -a" brings me to the same line, which just keeps being there for hours, stuck..

Thanks!

```
# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise
```

```
# uname -a
Linux oscillator 2.6.32-60-server #122-Ubuntu SMP Wed May 7 20:24:24 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by skipx on 2014-10-30
Nobody? Just feel a bit lost here ..

---

