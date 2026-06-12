---
title: "please help!!!  Problem with java jdk 1.6"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by alwar.sumit on 2007-10-02
i've  recently installed ubuntu 7.04 from a DVD. I install jdk1.6 on my pc and using terminal i wrote a program with .java extension.
i compiled it correctly and it runs correctly. after that i install Ecllipse IDE. after that i wrote another program in terminal......i compiles correctly but when i run it..it is giving the following exception: (my file name was sam.java )

Exception in thread "main" java.lang.ClassFormatError: sam (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)


please help me....what i have to do to make jdk rework correctly.

---

### Post by fvbakel on 2007-10-02
Hi,

It looks to me that you are not really using the java jdk 1.6 yet. Your trace file contains references to the gcj libs. I think the the gnu java version is your default java version.

You can check your current active version like this:
1. open a terminal

2. java -version

output should be like this:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


You can set the sun java as your default. This should be done like this:

1. list the java versions you have
update-java-alternatives -l

a line similar like this should be there:
java-6-sun 63 /usr/lib/jvm/java-6-sun

2. set the sun java as your default
update-java-alternatives -s java-6-sun


More information can be found here:
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

Good luck.

---

### Post by alwar.sumit on 2007-10-03
thanks u very much...................fvbakel

---

