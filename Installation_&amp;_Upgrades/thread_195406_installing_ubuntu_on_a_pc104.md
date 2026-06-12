---
title: "installing ubuntu on a pc104"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by odysseus.lost on 2006-06-12
Hi,

would it be possible to install ubuntu on a pc104 (Intel 166 MHz with 64 MB RAM), since ubuntu installation does not offer any way of selecting which components to install and I only need a 2.6.x kernel installed with no GUIs but with some development libraries and a few compilers.

Cheers

---

### Post by taurus on 2006-06-12
You can download and install the server version.  Then install gcc/make/etc. with
```

sudo apt-get install build-essential

```

---

### Post by odysseus.lost on 2006-06-21
[QUOTE=taurus]You can download and install the server version.  Then install gcc/make/etc. with
```

sudo apt-get install build-essential

```[/QUOTE]

Thanks that seemed to be the solution.

---

