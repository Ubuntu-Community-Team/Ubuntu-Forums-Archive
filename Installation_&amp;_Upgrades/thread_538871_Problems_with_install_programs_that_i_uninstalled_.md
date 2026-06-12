---
title: "Problems with install programs that i uninstalled in the past"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Y@M on 2007-08-30
Hello all.

I just installed Ubuntu, and i removed some softwares via the Synaptic like Gaim and OpenOffice.

When i try to install now the OpenOffice software, i get the error message:
> Error: Dependency is not satisfiable: openoffice.org-core

When i try to install the Pidgin software, i get the error message:
> Error: Dependency is not satisfiable: pidgin-data

How can i solve this problem?


Thanks you in advanced
Y@M

---

### Post by jeremyphares on 2007-08-30
do you have ubuntu-base installed? ive had problems like this in the past when i was missing ubuntu-base even though that wasn't the dependency that was listed as missing. also what are you using to install? synaptic should resolve dependencies for you, though make sure you have your package list is up to date. 
try to install "openoffice.org-core" and then install openoffice. if you cant use apt-get or synaptic than try [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

