---
title: "Java metapackages"
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FarJumper on 2009-07-13
Hi all,

I think there is a some fault with java packaging. We need a java metapackage (java-jre, java-jdk for example) which depends on one of supported JVM implementations (see below). I've seen packages ([https://bugs.launchpad.net/ubuntu/+source/libitext-java/+bug/396992](https://bugs.launchpad.net/ubuntu/+source/libitext-java/+bug/396992) for instance) which depend on specific java runtimes. This is quite ugly because sometimes user have to use some concrete java runtime. In that case there will be two of them installed in the system: one from package dependencies (gcj for instance) and the other - actually in use (sun-6 for instance).

Moreover, right now many *-java packages doesn't have any java jvm dependencies at all! I guess it was because of the above problem.

My vision of java metapackages:

"java-jre" metapackage:
Depends: gcj-jre | sun-java6-jre | sun-java5-jre | openjdk-6-jre | icedtea-6-jre-cacao

"java-jdk" metapackage:
Depends: gcj-jdk | sun-java6-jdk | sun-java5-jdk | openjdk-6-jdk


Bugreport created:
[https://bugs.launchpad.net/ubuntu/+bug/396999](https://bugs.launchpad.net/ubuntu/+bug/396999)
Please comment

---

### Post by Starks on 2009-07-13
Browser plugins should be included in the meta.

---

### Post by dinxter on 2009-07-13
at the moment java dependencies are provided by a number of virtual-packages that show support for various java standards and so on of the form,

> $ apt-cache show default-jre|grep Provides
Provides: java-runtime, java2-runtime, java5-runtime, java6-runtime


$ apt-cache show sun-java6-jre|grep Provides
Provides: java-runtime, java-runtime-headless, java-virtual-machine, java2-runtime, java2-runtime-headless, java5-runtime, java5-runtime-headless, java6-runtime, java6-runtime-headless

$ apt-cache show openjdk-6-jre|grep Provides
Provides: java-runtime, java2-runtime, java5-runtime, java6-runtime
so that packages should in theory depend on the a relevant java virtual-package that shows the java standards it requires. such as,
> $ apt-cache show libservlet2.4-java|grep Depends
Depends: default-jre-headless | java1-runtime-headless | java2-runtime-headless
whether thats the best way to do it is in the eye of the beholder i suppose but the virtual-packages are there for other java packages to use

[EDIT] sorry, by meta packages i meant virtual packages

---

### Post by dinxter on 2009-07-13
> **Starks said:**
> Browser plugins should be included in the meta.

default-jre pulls in openjdk-6-jre which in turn pulls in the relevant browser plugin icedtea6-plugin {EDIT] only 'suggests' though

---

### Post by FarJumper on 2009-07-13
dinxter, thanks for clarification. I didn't know about these virtual packages.

---

### Post by Starks on 2009-07-13
Eh?

I thought icedtea6-plugin and sun-java6-plugin were different.

---

