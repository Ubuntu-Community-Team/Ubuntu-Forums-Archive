---
title: "Installed latest Java, but don't know how to add it to PATH!"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by shaggy999 on 2007-08-24
Ok,  so I installed Java 6 via repos, but the installer didn't automatically set up my path.

 which java produces
/usr/bin/java

java --version produces
java version "1.4.2

Java6 was placed  /usr/lib/jvm

ls /usr/lib/jvm

java-1.4.2-gcj-4.1-1.4.2.0  java-1.5.0-sun-1.5.0.11  java-6-sun-1.6.0.00
java-1.5.0-sun              java-6-sun               java-gcj


How do I get java6 to be invoked instead of 1.4.2 when I run java apps? Frostwire refuses to run. :(

---

### Post by tiendn on 2007-08-25
you try: $sudo update-alternatives --config java

---

