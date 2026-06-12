---
title: "How to control minor version of Java (openjdk-6)"
date: 2015-02-27
forum: Installation &amp; Upgrades
---

### Post by jamal6 on 2015-02-27
Hi, I ran into a problem with openjdk 1.6 where my application worked fine with version 6b33-1.13.5-1ubuntu0.12.04 but does not with 6b34-1.13.6-1ubuntu0.12.04.1.  When I install openjdk, is it possible to install and fix the version of it to a particular minor version?  I normally do the install like such:

apt-get install openjdk-6-jdk

however, when I try this, I get an error.

apt-get install openjdk-6-jdk=6b33-1.13.5-1ubuntu0.12.04Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Version '6b33-1.13.5-1ubuntu0.12.04' for 'openjdk-6-jdk' was not found

---

