---
title: "Help in installing yafray renderer"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by msadiqrajani on 2007-09-24
Hi guys,
I have downloaded yafray renderer for ubuntu.When i run deb file it gives error.
version is **yafray_0.0.9-exr_i386.deb**
Error:**Dependency is not satisfiable: libc6**.

---

### Post by loell on 2007-09-24
where did you get that package?

there is one in the repo

```
sudo apt-get install yafray
```

---

### Post by msadiqrajani on 2007-09-26
i have downloaded from official yafray site
it is giving error of missing package

[B]admin@admin-desktop:~$ sudo apt-get install yafray
Password:
Reading package lists... Done
Building dependency tree... Done
Package yafray is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package yafray has no installation candidate
admin@admin-desktop:~$[/B]

which package i need to install

---

### Post by loell on 2007-09-26
uhmm, ok. which version of ubuntu are you using?

---

### Post by iconicmoronic on 2007-09-27
ig2kuvsaeihbmuw.cul

---

### Post by msadiqrajani on 2007-09-27
I Am Using Ubuntu 6.06 Lts

---

### Post by loell on 2007-09-27
i see, the deb package you installed is not meant for ubuntu 6.06 , if you really want  yafray  might as well move to a newer ubuntu release example (ubuntu 7.04 , ubuntu 7.10).

with these versions, you can install yafray, by just typing this in the command line console

```
sudo apt-get install yafray
```

---

### Post by msadiqrajani on 2007-09-28
missing package errer
which package is required for installing yafray

---

### Post by loell on 2007-09-28
it seems that we do not understand each other.

good luck...

---

