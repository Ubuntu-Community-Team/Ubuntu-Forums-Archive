---
title: "java -version trubble"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by NIKOSHIBA on 2007-04-21
hi
i have installed from repos sun-java packages. they are listed in repos as version 1.5. but when i run "java -version" i get output version 1.4.2
what's wrong with that? i need 1.5.10! is it not in the repos?

---

### Post by taurus on 2007-04-21
Do you see version 1.5 on this list when you run this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by NIKOSHIBA on 2007-04-21
> **taurus said:**
> Do you see version 1.5 on this list when you run this command from a terminal?

```
sudo update-alternatives --config java
```

thnx taurus

it gave me this:
```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```

i chose 3 (version 1.5.11. and now output is very satisfactory. 
could you also tell me how can i get same result but now with javac.
" javac -version" suppose to give me "version 1.5.11". but i get:
```
Eclipse Java Compiler v_686_R32x, 3.2.2 release, Copyright IBM Corp 2000, 2006. All rights reserved.

```

---

### Post by djr on 2007-04-21
Try
```
sudo update-alternatives --config javac
```

---

