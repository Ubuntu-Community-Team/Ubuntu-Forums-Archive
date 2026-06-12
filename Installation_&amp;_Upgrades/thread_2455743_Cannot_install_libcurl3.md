---
title: "Cannot install libcurl3"
date: 2020-12-26
forum: Installation &amp; Upgrades
---

### Post by mighty-platypus on 2020-12-26
Good morning / afternoon / evening

So I want to install OpenLieroX but it says that I need to install libcurl3.
When I'm trying to install it, it says that it's no longer available and replaced by libcurl4.
However OLX don't want to be installed with libcurl4.

My OS is Ubuntu 20.04.1 LTS

What am I supposed to do ?

Grateful,
Ivan

---

### Post by ActionParsnip on 2020-12-26
Try:
```

sudo apt install libcurl3-gnutls libcurl3-nss

```

---

### Post by mighty-platypus on 2020-12-26
Worked, thank you.

---

