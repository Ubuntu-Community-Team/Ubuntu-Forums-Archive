---
title: "I can not install anything using apt-get install ."
date: 2014-10-01
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2014-10-01
I have had problem with user, then I did create a new one but the problem is now.
For examples.
sudo apt-get install libudev-dev 
[sudo] password for test: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libudev-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libudev-dev' has no installation candidate
-------------------------------------------------------------------------------------------
This error happend each time I try to install a package.
------------------------------------------------------------------------------------
When I open Software source on unity panel, then click on edit.. Software Sources fane is grey.. is not active.

---

### Post by ian-weisser on 2014-10-01
The libudev-dev package does exist, and is in the 'main' repository for all currently-supported versions of Ubuntu.

1) Go to System Settings --> Software & Updates --> Ubuntu Software tab

Is the 'Canonical-supported free and open-source software (main)' checkbox selected?
If not, select it and try installing again.


2) Open a terminal and try:
```
sudo apt-get update
```
Is the package database refresh successful? Are there any errors?

---

