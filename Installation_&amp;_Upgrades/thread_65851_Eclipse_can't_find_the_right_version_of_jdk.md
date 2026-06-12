---
title: "Eclipse can't find the right version of jdk"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by CastorTroy on 2005-09-15
Hi,

I installed the java 1.5 jdk and eclipse. However, when I go to start eclipse, it says:
Required Java version: 1.4.1. Available: 1.4
I know I have the 1.5 installed, and I looked all over my computer and can't find another version. Does anyone know what is going wrong?

---

### Post by tsvetan on 2005-09-15
Hi,

1. You can check your java version by using "#java -version". (just to be sure)

2. You can specify the java virtual machine to be used by eclipse in this way:

eclipse -vm "/path_to_java_installation/bin/java"


I hope this can help you.

---

### Post by CastorTroy on 2005-09-18
Yea, that worked. Thanks!

---

