---
title: "installation problem"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by blufade on 2007-08-22
hi
why do i get this error message whenever i  install a new package ??

```
E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured
```

---

### Post by heimo on 2007-08-22
> **blufade said:**
> hi
why do i get this error message whenever i  install a new package ??

```
E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured
```

Try reinstalling of clvm.

I'd run:
```

sudo apt-get clean
sudo apt-get update
sudo apt-get --reinstall install clvm
sudo apt-get -f install

```EDIT: If that doesn't work. Try purging it first and then rerunning what's above.
```
 sudo apt-get --purge remove clvm
```


EDIT: Added "install"

---

### Post by blufade on 2007-08-22
this is what i get
```
root@xxxx-desktop:~# sudo apt-get --reinstall clvm
E: Invalid operation clvm
root@xxxx-desktop:~# 

```

---

### Post by heimo on 2007-08-22
My mistake.
```
sudo apt-get --reinstall **install** clvm
```

---

