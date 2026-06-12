---
title: "OpenJDK is default, instead of Sun's Java 6. How do I change that?"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by MadsHorndrup on 2010-09-04
I'm a software developer, and I like programming in Java.
I also like NetBeans, but when I installed it OpenJDK automaticly installed aswell and became default.
That wouldn't be a problem if I could just uninstall it, but it turns out that if I uninstall OpenJDK I also remove NetBeans :(

I do have regular Java installed. How do I change the default back to Sun's Java 6, and/or get rid of OpenJDK for good?

Thanks in advance.

---

### Post by lykeion on 2010-09-04
I also enjoy programming in Java :-)
And BTW have you tried _[IntelliJ IDEA]("http://www.jetbrains.com/idea/free_java_ide.html")_? I find it's a very good IDE for Java.

Back to your question, I'd do it like this:

1) uninstall NetBeans

2) remove OpenJDK packages
Synaptic > search for "openjdk" > uninstall all installed packages starting with "openjdk-6"

3) enable partner repository
Synaptic > Settings > Repositories > Other Software tab > check partner repository (at top)
Click Reload

4) install Sun Java JDK
Synaptic > search for "sun-java6" > install sun-java6-jdk

5) install NetBeans

---

### Post by howefield on 2010-09-04
> **MadsHorndrup said:**
> I do have regular Java installed. How do I change the default back to Sun's Java 6, and/or get rid of OpenJDK for good?

They should co-exist peacefully together as far as I can see. But to set the default.

```
sudo update-alternatives --config java
```

---

