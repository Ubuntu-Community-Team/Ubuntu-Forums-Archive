---
title: "Sub-process /usr/bin/dpkg returned an error code (2)  „libdbus-glib-1-2“"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by rado3105 on 2011-11-28
I have ubuntu 10.04, I cant install or upgrade because of some problem with: „libdbus-glib-1-2“

---

### Post by zvacet on 2011-11-29
Can you post output of

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by raja.genupula on 2011-11-29
> **rado3105 said:**
> I have ubuntu 10.04, I cant install or upgrade because of some problem with: „libdbus-glib-1-2“


open synaptic package manager and fix that broken package , if its gave you problem then remove and reinstall it .

---

### Post by rado3105 on 2011-12-02
Do you want to continue [Y/n]? y
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libdbus-glib-1-2': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
r-c@r-c-desktop:~$

---

