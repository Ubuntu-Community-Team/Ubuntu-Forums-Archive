---
title: "where is gcc?"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by vadriaan on 2006-11-10
So far I was very happy with this distribution (6.06) until I needed to compile a file. 

ogre@four:~$ gcc --version
bash: gcc: command not found

According to the package manager gcc is installed. Searching for gcc lists all the libraries but no executable.

Synaptic reports the following installed files:
/usr/share/doc/gcc-4.0-base
/usr/share/doc/gcc-4.0-base/changelog.gz
/usr/share/doc/gcc-4.0-base/TODO.Debian
/usr/share/doc/gcc-4.0-base/copyright
/usr/share/doc/gcc-4.0-base/.copyright
/usr/share/doc/gcc-4.0-base/README.Debian.gz
/usr/share/doc/gcc-4.0-base/changelog.Debian.gz
/usr/share/doc/gcc-4.0-base/.changelog.Debian.gz

---

### Post by ciscosurfer on 2006-11-10
Install **build-essential**

---

### Post by vadriaan on 2006-11-10
Would have done it if the option was availabe. Synaptic claims everyting on the DVD is installed.

---

### Post by taurus on 2006-11-10
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo aptitude update
sudo aptitude install build-essential
```
Build-essential doesn't get installed as default so you have to install it by hand!

---

