---
title: "Install server and not destroy desktop"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by wifiabc on 2006-06-30
I hv installed desktop version of ubuntu 606. How do I go about upgrading it to include the server components and still retain the desktop?

---

### Post by pbw on 2006-06-30
```

sudo apt-get update
sudo apt-get install whatever

```just install the packages you want, replacing whatever with uhh.. whatever ;). eg. php, apache2, mysql, proftp etc. and ```

sudo apt-get install ubuntu-desktop

```
or
```

kubuntu-desktop

```
or
```

xubuntu-desktop

```
Depending on your DE

---

