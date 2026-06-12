---
title: "&quot;Error: Dependency is not justifiable: libglib 1.2&quot;."
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by drz4007 on 2008-11-15
Hello. I am trying to istall a *.deb* package and i keep getting the message **"Error: Dependency is not justifiable: libglib 1.2".** I installed through  the synaptic all the packages that are related to libglib, but i keep getting the same message. The package i am trying to install is on a cd and it is a digital dictionary (if that helps). 


When i try to install it in a terminal i get this:

va@va-desktop:~/Desktop$ sudo dpkg -i mgde_2006_i386.deb
Selecting previously deselected package mgde.
(Reading database ... 136917 files and directories currently installed.)
Unpacking mgde (from mgde_2006_i386.deb) ...
dpkg: dependency problems prevent configuration of mgde:
mgde depends on libgdk-pixbuf2 (>= 0.22.0); however:
Package libgdk-pixbuf2 is not installed.
mgde depends on libglib1.2 (>= 1.2.0); however:
Package libglib1.2 is not installed.
mgde depends on libgtk1.2 (>= 1.2.10-4); however:
Package libgtk1.2 is not installed.
dpkg: error processing mgde (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:


However, when i try to install all these "missing" packages i get the message that all of them are installed and up-to-date.

Any clues??

---

### Post by pigphish on 2009-11-03
same problem I got it to work by using alien on the rpm package. I still get freezing issues though. 

Support is fairly bad from magenta in general on all these issues. Took me a weak to get it registered. 

However, there is not better dictionary in my search.

---

