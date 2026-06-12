---
title: "apache default installation"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by aderama on 2006-12-04
After fooling around with different apache/mysql installations (apt-get, vhcs, lamp, ...) my web-server ended up in a mess. ](*,) Now I have no idea how to restore the default installation with php5 and home-dirs for each user. Is there any possibility to completely remove and reinstall a package with apt-get? ("apt-get remove" does not remove the installation and therefore "apt-get install" does not install anything after "apt-get remove")

---

### Post by an.echte.trilingue on 2006-12-04
```
dpkg purge your_package
```

should do the trick, although I must confess that I am unfamilar with this particular set of packages...

---

### Post by aderama on 2006-12-04
Thank you for your fast reply, unfortunately he still wants to reuse the previous installation without writing executables or configuration files.

```

Preconfiguring packages...
Selecting previously deselected package apache2.
(Reading database [...])
Unpacking apache2 (from [...])
Setting up apache2 (...)

```

---

### Post by aderama on 2006-12-06
does anyone know where the list of currently and previous installed dpkges is stored?

---

