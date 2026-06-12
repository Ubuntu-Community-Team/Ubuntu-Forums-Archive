---
title: "Installing tomcat5 package without gcj dependency"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by gfarrow on 2006-08-14
I have installed sun-java-* and I want to install the tomcat5 package.  However this package has a dependency on gcj which has numerous other dependencies until it wants to install a couple of hundred of dependent packages.  Tomcat5 should not require anything besides the sun java packages.  

How can I install tomcat5 from the package without all of these unnecessary dependencies?

---

### Post by clanie on 2006-08-18
aptitude install sun-java5-jdk
update-alternatives --config java
aptitude install tomcat5

At least that used to work.
Tried it today with a new install of 6.06.1, and it failed with lots og unsatisfied dependencies.

---

### Post by bricktop on 2006-08-23
Hi, I am hiving the same problem, Tried the above but apt still wants to install the dependencies. Any idea how to install tomcat so it uses the sun jdk only and not the hundreds of others?

---

### Post by Gustavo Orair on 2006-09-26
You should use apt-get install instead of aptitude

---

### Post by EmmEff on 2007-05-21
Any update on this?  Seems like Feisty even has a gcj dependency...

---

