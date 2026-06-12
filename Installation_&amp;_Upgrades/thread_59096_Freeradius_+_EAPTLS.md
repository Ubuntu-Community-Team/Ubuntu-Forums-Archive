---
title: "Freeradius + EAP/TLS"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by cnlohfin3109 on 2005-08-22
Working off a fresh install of 5.04.  just got updates and used synaptic to install freeradius.  uncommented the lines in the eap.conf for setting up ttls(so also tls) when i ran
```
freeradius -X
```

i get the following error

```
...
...
...
rlm_eap: Loaded and initialized type gtc
rlm_eap: Failed to link EAP-Type/tls: rlm_eap_tls.so: cannot open shared object file: No such file or directory
radiusd.conf[9]: eap: Module instantiation failed.

```

most of the things where ive seen this suggests re-compiling with 

```
./configure --disable-shared 
```

but is there anyway to get this to work from the repositories?  i ran into another bees nest downloading and tring to compile the source myself

Thanx,
Chris

---

### Post by cnlohfin3109 on 2005-08-24
Ok, for anyone else with this problem. in order to get it to compile i needed the following

```
./configure --without-rlm_x99_token --disable-shared --sysconfdir=/etc/
make && make install
```

unfortunately now im having a problem with radiusd stalling after initializing gtc... if i get it working ill post solution... kinda at a loss though  ](*,)

---

