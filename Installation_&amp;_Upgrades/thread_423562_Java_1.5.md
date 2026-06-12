---
title: "Java 1.5"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by JimmyJames88 on 2007-04-26
I keep trying to install Java 1.5 to run limewire everytime I try a guide on it it still doesnt work.  

When I type java -version in console it still comes up as a previous version, any help would be much appreciated.

---

### Post by zvacet on 2007-04-26
Install it with synaptic.in the search box type **sun** and you will find it if you have all repos open.

---

### Post by JimmyJames88 on 2007-04-26
Im not seeing Java 1.5 anywhere, I see things like Java 5.0 and Java 6.0 type packages.

---

### Post by taurus on 2007-04-26
Java 5.0 = 1.5
Java 6.0 = 1.6

---

### Post by JimmyJames88 on 2007-04-26
I just uninstalled all of the java packages, and then i installed the sun-java5-bin and sun-java-jre packages, I goto my console after the install goes successfully and guess what:

```
james@MESA3202:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
james@MESA3202:~$ 

```

still coming up as version 1.4.2

---

### Post by taurus on 2007-04-26
What happens if you run this command from a terminal?  Do you see version 1.5 on the list?  If you do, make sure you make it as a default version.

```
sudo update-alternatives --config java
```

---

### Post by JimmyJames88 on 2007-04-26
Awesome, thanks Taurus I heart you!:lolflag:

---

