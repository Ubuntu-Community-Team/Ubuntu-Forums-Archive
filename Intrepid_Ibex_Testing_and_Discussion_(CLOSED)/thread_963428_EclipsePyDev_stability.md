---
title: "Eclipse/PyDev stability?"
date: 2008-10-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by decoherence on 2008-10-30
Eclipse/PyDev keep crashing at seemingly random points. It becomes unresponsive and I have to force quit it. I think it may have something to do with the syntax checking but I'd have to see it more to be sure.

Anyone else?

> JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 778018
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

---

### Post by decoherence on 2008-10-30
I replaced GJC with Sun Java and haven't had any more problems.... faster, too...

---

