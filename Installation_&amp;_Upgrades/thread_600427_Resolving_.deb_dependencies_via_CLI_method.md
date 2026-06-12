---
title: "Resolving .deb dependencies via CLI method?"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by perixx on 2007-11-02
Hello!

Does anyone know a tool to check and list the dependencies of a .deb package?


perixx

---

### Post by ruibernardo on 2007-11-02
Hi penrixx,

if you downloaded one deb file, whether it is from a repository or just a single deb file from elsewhere (an opensource website that has a compiled deb file, for example), run:

```
dpkg --info deb_file_name.deb
```This will display the information about it, with a section named "Depends".

To list the dependencies from a package in the repositories, simulate its installation like this (apache2 is an example):

```
sudo apt-get --simulate install apache2
```This will list all the packages you need to download and install.

---

### Post by perixx on 2007-11-03
Thank you epemeteo!


Actually I'm having some trouble getting pre-compiled .deb packages to work (like the latest Gnome-Commander) - I know it might not work because it's not specifically compiled for Ubuntu; so,

this is what I really want to do!

Compile things from source -- the problem is that I always get messages about missing packages and stuff, but 
reviewing config.logs brought me only just so far :-.
(I made SOME progress, but somehow I just can't finish my task) - and yes, I have 'build-essential' installed.

Mostly, I come across some non-resolvable dependency issue like described here:
> [http://ubuntuforums.org/showthread.php?t=599482](http://ubuntuforums.org/showthread.php?t=599482)

Do you also know a way to check dependencies for source-packages and how to resolve them?


perixx

---

### Post by zvacet on 2007-11-03
```
sudo apt-get build-dep package_name
```

---

### Post by perixx on 2007-11-04
> Do you also know a way to check dependencies for source-packages and how to resolve them?

(I mean to compile from source, e.g. *.tar.bz2)

> sudo apt-get build-dep package_name 

Will this also work for source-tarballs or only for .deb's?


perixx

---

