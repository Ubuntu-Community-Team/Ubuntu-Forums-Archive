---
title: "install adobereader"
date: 2015-09-30
forum: MINT
---

### Post by Cristian1969 on 2015-09-30
I trye install adobereader in mint 17.1. ```
sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release -sc)partner"
``` I have this message ```
sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release -sc)partner"
```

---

### Post by lisati on 2015-09-30
Not a *Cafe* discussion
*Thread moved to **MINT**.*

---

### Post by PaulW2U on 2015-09-30
Cristian1969, the terminal command that you're using implies the addition of a PPA but you're not adding a PPA. You're adding a Canonical/Ubuntu repository. Confusing isn't it?

I have no idea what changes Mint makes to Ubuntu but personally I would add:
```

deb http://archive.canonical.com/ubuntu xxx partner

```to /etc/apt/sources.list where xxx is whatever Ubuntu release your version of Mint is based on. Trusty? Then:
```
sudo apt-get update
```
and you should be able to install adobe reader.

Hope that helps or at least points you in the right direction. :)

---

