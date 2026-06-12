---
title: "Sun Java 6"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by ferulebezel on 2011-06-16
For some reason Sun Java 6 isn't in any of the standard repositories.  Some sites recommend adding the old Maverick repositories to install it.  I just know that adding an old repository is going to break something.  Does anyone know when it will be in the standard repositories?

---

### Post by dFlyer on 2011-06-16
> **ferulebezel said:**
> For some reason Sun Java 6 isn't in any of the standard repositories.  Some sites recommend adding the old Maverick repositories to install it.  I just know that adding an old repository is going to break something.  Does anyone know when it will be in the standard repositories?

Sun Java 6 is in the repositories. You may need to add the canonical Partners repository. To do so start software center goto edit software sources other software and add it. Update the archives and it should be there.

---

### Post by tommcd on 2011-06-16
I used to always install the Sun java on previous versions of Ubuntu; but I have found that the *openjdk* that comes with Ubuntu 11.04 works well enough for using websites that require java.
If you do install the Sun java, you should probably remove the openjdk that comes with 11.04 in order to avoid potential conflicts.

---

### Post by heldal on 2011-06-16
openjdk sadly doesn't work with many online applications. Network banking is typically a black hole for anything other than sun-java. Sun-java is available in the partners repository as mentioned previously. It is however not being updated as frequently as it should. For the last couple weeks browsers have been complaining that the currently installed version 6 update 24 is insecure and outdated. The current sun-java version 6 update 26 has not yet found its way to the repositories

---

