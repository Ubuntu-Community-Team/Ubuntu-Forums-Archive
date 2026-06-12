---
title: "iReport is not working"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by ghf on 2008-04-08
Hi all 
I installed iReport that uses JasperReports in Ubuntu 7.10 gutsy
from this repository

[http://srvremi.free.fr/ubuntu](http://srvremi.free.fr/ubuntu)

and its dependencies are :
sun-java6-jre
bubuntu-common
and the last one is available in ireport repository

but when I launch the application this error message appears in the termi[SIZE="1"]nal:
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/jdesktop/swingx/JXTable (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
        at it.businesslogic.ireport.gui.ValuesDialog.initAll(ValuesDialog.java:78)
        at it.businesslogic.ireport.gui.ValuesDialog.<init>(ValuesDialog.java:66)
        at it.businesslogic.ireport.gui.MainFrame.<init>(MainFrame.java:532)
        at it.businesslogic.ireport.gui.MainFrame.main(MainFrame.java:8016)[/SIZE]

they said in this site :
[http://www.jasperforge.org/index.php?option=com_joomlaboard&Itemid=215&func=view&catid=9&id=29576]("http://www.jasperforge.org/index.php?option=com_joomlaboard&Itemid=215&func=view&catid=9&id=29576")
that the problem is from java version 
but I modified the path of JAVA_HOME to /usr/lib/jvm/java-6-sun-1.6.0.03

so What is the problem ??:confused:

---

