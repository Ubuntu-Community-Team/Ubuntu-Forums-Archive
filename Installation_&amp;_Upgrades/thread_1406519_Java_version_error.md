---
title: "Java version error"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by subakaran on 2010-02-14
Hi 
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts,

Using this command , I installed java successfully.
so now i want to test first.
I typed java version command in terminal

But i got error.

ERROR REPORT:
--------------------------

Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: version.  Program will exit.

---

### Post by byStanderone on 2010-02-14
...visit this thread: [http://ubuntuforums.org/showthread.php?t=1400351](http://ubuntuforums.org/showthread.php?t=1400351)

---

### Post by jocko on 2010-02-14
> **subakaran said:**
> Hi 
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts,

Using this command , I installed java successfully.
so now i want to test first.
I typed java version command in terminal

But i got error.

ERROR REPORT:
--------------------------

Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: version.  Program will exit.
That's because "java version" is not the correct command. Try:```
java -version
```

---

### Post by subakaran on 2010-02-14
Hi,
Thankss.

Actually by mistake I typed wrong command java version.

Correct command:java -version.

I missed -(HYPHEN) before version command.

Thanks for your reply

---

