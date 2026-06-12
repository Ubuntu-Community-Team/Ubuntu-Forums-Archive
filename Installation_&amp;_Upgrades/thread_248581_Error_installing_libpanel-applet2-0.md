---
title: "Error installing libpanel-applet2-0"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by schorem on 2006-09-01
Hi there,

I recently installed Ubuntu on my desktop. But when I wanted xgl and compiz I got an error when it tried to install libpanel-applet2-0.

```
...
dpkg: ontleedfout, in bestand `/var/lib/dpkg/status' bij regel 7691 pakket `libpanel-applet2-0':
 `Depends'-veld, ongeldige pakketnaam `libgnomecanvas2-0$': teken `$' niet toegestaan - slechts letters, cijfers en -+._ toegestaan
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

It is in Dutch, but what it basicly says is: There is an error at line 7691 in package 'libpanel-applet2-0':
 'Depends'-field, illegal packagename 'libgnomecanvas2-0$': character '$' not allowed .... etc.

How can I fix this. apt-get -f install doesn't seem to help....

---

