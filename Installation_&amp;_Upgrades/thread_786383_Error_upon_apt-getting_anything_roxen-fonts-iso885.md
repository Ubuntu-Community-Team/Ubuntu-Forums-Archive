---
title: "Error upon apt-getting anything: roxen-fonts-iso8859-2"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by Eax.exe on 2008-05-08
Hello :)

I played around with XFCE, but upon installation of the package  "roxen-fonts-iso8859-2"
It gave me a couple of errors which I ignored.

Not EVERY! time I try to apt-get something it says:
```

Setting up roxen-fonts-iso8859-2 (0-9) ...
Roxen is not configured yet, aborting
dpkg: error processing roxen-fonts-iso8859-2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 roxen-fonts-iso8859-2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone help me fix this?

---

### Post by lemming465 on 2008-05-10
First I'd try *apt-get update --fix-broken*.  If that has no useful effect, I'd next try *apt-get remove --purge roxen-fonts-iso8859-2*.  If that doesn't do it either, it would take some serious research to figure it out.

---

