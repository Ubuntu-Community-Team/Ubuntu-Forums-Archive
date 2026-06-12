---
title: "unmet dependencies for postgresql-contrib-8.3 and postgresql-plperl-8.3"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by irfans on 2011-04-21
I am getting the following errors while installing packages,
 **postgresql-contrib-8.3**
 **Error** - The following packages have unmet dependencies:
  postgresql-contrib-8.3: Depends: libossp-uuid15 but it is not installable
E: Broken packages

 **postgresql-plperl-8.3**
 **Error** - The following packages have unmet dependencies:
  postgresql-plperl-8.3: Depends: libperl5.8 (>= 5.8.8) but it is not going to be installed
E: Broken packages

 Any help appreciated..

---

### Post by zvacet on 2011-04-25
In terminal 

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

