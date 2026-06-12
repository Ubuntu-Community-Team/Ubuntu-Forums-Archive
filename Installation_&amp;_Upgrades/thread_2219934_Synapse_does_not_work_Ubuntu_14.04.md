---
title: "Synapse does not work Ubuntu 14.04"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by Derelinquat fenestras on 2014-04-26
Hello all,

Just upgraded to Ubunntu 14.04 LTS from 12.04 LTS running Ubuntu Studio flavor.   Loved the application Synapse for launching applications and searching my machine...
Unfortunately since I updated to 14.04, it seems that it has been unninstalled and when I tried to reinstall it via PPA, I get the output:

```
Package synapse is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'synapse' has no installation candidate



```

Does anyone know of a way to make it work under 14.04 or know of a similar application?

Thank you in advance!

---

### Post by lifelike27 on 2014-04-30
There isn't a synapse build for 14.04 yet, but if you really want it now, you can grab it from their testing ppa (bleeding edge): 

```
sudo apt-add-repository ppa:synapse-core/testing
```

Don't forget, this is bleeding edge, everything won't work. It's your responsibility, etc.

---

### Post by anujmonster on 2014-05-08
> **lifelike27 said:**
> There isn't a synapse build for 14.04 yet, but if you really want it now, you can grab it from their testing ppa (bleeding edge): 

```
sudo apt-add-repository ppa:synapse-core/testing
```

Don't forget, this is bleeding edge, everything won't work. It's your responsibility, etc.

Just installed on a fresh install of 14.04.  Works like a charm.

---

### Post by brinesalt on 2014-05-23
I just tried this, but can't find the app anywhere or figure out any way to start it? probably missing something very obvious..

---

### Post by markodd on 2014-12-13
> **brinesalt said:**
> I just tried this, but can't find the app anywhere or figure out any way to start it? probably missing something very obvious..

Hey!

You need to do:

```
sudo apt-get update
```

Followed by:

```
sudo apt-get install synapse
```

---

