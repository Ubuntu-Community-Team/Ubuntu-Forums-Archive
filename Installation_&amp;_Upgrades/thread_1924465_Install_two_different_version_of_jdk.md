---
title: "Install two different version of jdk"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by mertoz on 2012-02-12
A project that I want to compile requires javad jdk 1.5. On my ubuntu there is installed a java jdk 1.6. What is the procedure to install both of them not to run over my 1.6 version? On the sun site there is just an bin installation file..

---

### Post by winh8r on 2012-02-12
the 1.6 version should do everything that the 1.5 version did so there should be no problem compiling using 1.6.

the only time there would be a problem would be trying to compile using an older version of java than the package requires

---

### Post by mertoz on 2012-02-13
The problem is that project is doing the java check and if I point it to openjdk-1.6 it fails with an error that i need java 1.5..

---

### Post by winh8r on 2012-02-13
It is not generally advisable to use older versions of Java than are currently available due to bugfixes and security fixes being in the newer version.

But this might help you for now :

[http://ubuntuforums.org/showthread.php?t=1656409&highlight=java+version]("http://ubuntuforums.org/showthread.php?t=1656409&highlight=java+version")

---

