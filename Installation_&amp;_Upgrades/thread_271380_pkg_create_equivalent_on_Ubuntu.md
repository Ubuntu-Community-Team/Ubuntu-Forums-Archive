---
title: "pkg_create equivalent on Ubuntu"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by smyru on 2006-10-04
Is it possible to create a .deb package file from an installed package? I mean a situation reverse to installing a deb binary. 

I am searching for a tool/solution that would work like FreeBSD's pkg_create tool. It takes files of installed package, its infrastructure (install scripts, etc.) and creates a binary package (.tbz), that one can copy to another system f.e.

---

### Post by K.Mandla on 2006-10-04
Is this of any use to you?

[https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch)

---

### Post by smyru on 2006-10-10
Unfortunately not. What you linked here is a description how to build a package. I don't want to create, build, compile a new package. I want to well, backup(?) an installed package(s). Make it a .deb again.

---

### Post by smyru on 2006-11-06
Solution found: [aptoncd.sourceforge.net]("http://aptoncd.sourceforge.net/"). It is a nice try, but I am still searching for something lightweight and console based.

---

### Post by smyru on 2007-02-20
For the record. Here is a solution I was seeking:

Re-creating Debian binary packages with dpkg-repack
[http://www.debian-administration.org/articles/499](http://www.debian-administration.org/articles/499)

---

