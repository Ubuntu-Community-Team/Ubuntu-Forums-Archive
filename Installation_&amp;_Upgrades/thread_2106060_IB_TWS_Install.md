---
title: "IB TWS Install"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by deeperinits on 2013-01-17
Have seen the thread here, and can someone help explain this error message? 

Thanks

____@ubuntu:~$ cd IB
____@ubuntu:~/IB$ java -cp jts.jar:hsqldb.jar:jcommon-1.0.12.jar:jfreechart-1.0.9.jar:jhall.jar:other.jar:rss.jar -Xmx512M -XX:MaxPermSize=128M jclient.LoginFrame .
Exception in thread "main" java.lang.NoClassDefFoundError: jclient/LoginFrame
Caused by: java.lang.ClassNotFoundException: jclient.LoginFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: jclient.LoginFrame. Program will exit.
____@ubuntu:~/IB$

---

