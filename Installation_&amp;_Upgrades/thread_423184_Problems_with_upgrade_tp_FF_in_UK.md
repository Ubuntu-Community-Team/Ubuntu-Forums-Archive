---
title: "Problems with upgrade tp FF in UK"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by uk144 on 2007-04-25
My installation fails at 

Failed to fetch [http://apt.agnula.org/demudi/dists/testing/local/binary-i386/Packages.gz](http://apt.agnula.org/demudi/dists/testing/local/binary-i386/Packages.gz) 404 Not Found

Is this because the server is overloaded or is there a more serious problem?

I get this error no matter when or which day I attempt the upgrade from 6.10

---

### Post by zvacet on 2007-04-26
Comment (put 3 sign in front of line) that line in your source list.In fact you should comment all unofficial repos before upgrade.Your Edgy must be up-to-date so

```
sudo aptitude update
```

---

