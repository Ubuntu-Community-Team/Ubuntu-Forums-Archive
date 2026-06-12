---
title: "Sun's JRE: Am I missing something?"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by qbproger on 2007-03-20
I installed Sun's java jre from the repositories (1.5.0.08).  I had to relink the java in /usr/bin/java to the correct java after tracking down where it was installed.  It was linked to gij which didn't support what i was trying to run.  I was just wondering if there is an easier way to reset which jvm to use than deleting the symbolic link and creating a new one because this seems rather advanced for new users wanting to use java.

Any enlightenment is appreciated.

---

### Post by T_W on 2007-03-20
Check out the update-java-alternatives command.

This can be  reconfigure the /etc/alternatives system to use Sun's JRE rather than gij.

---

