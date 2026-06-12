---
title: "debootstrap question"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Bothered on 2007-10-31
Does anyone know exactly which meta packages are installed with the following command:

```
sudo debootstrap gutsy [target] [mirror]
```

Is it just ubuntu-minimal?Packages are retrieved that aren't listed on the ubuntu-minimal dependency list.

---

### Post by ruibernardo on 2007-11-01
Hi,

debootstrap does install ubuntu-minimal, but also some other things. You can see what debootstrap installs and do on the script for the release you selected. 

The scripts are located at /usr/lib/debootstrap/scripts/.

---

