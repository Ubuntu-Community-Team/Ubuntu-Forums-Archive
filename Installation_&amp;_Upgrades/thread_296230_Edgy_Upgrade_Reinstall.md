---
title: "Edgy Upgrade Reinstall"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by Rick Myers on 2006-11-09
I ran the upgrade from Dapper to Edgy last night and had a few error messages. I used;

gksu &#8220;update-manager -c &#8221;

Is there is a way to reinstall the upgrade?

---

### Post by an.echte.trilingue on 2006-11-09
using the command line, 

```
sudo gedit /etc/apt/sources.list
```

make sure you are pointing to the correct edgy repositories. Then

```
sudo apt-get update
sudo apt-get dist-upgrade
```

then reboot

Take care,
-mat

---

### Post by Rick Myers on 2006-11-09
> **an.echte.trilingue said:**
> using the command line, 

```
sudo gedit /etc/apt/sources.list
```

make sure you are pointing to the correct edgy repositories. Then

```
sudo apt-get update
sudo apt-get dist-upgrade
```

then reboot

Take care,
-mat

Thanks Mat. I'll give that a whirl.

---

