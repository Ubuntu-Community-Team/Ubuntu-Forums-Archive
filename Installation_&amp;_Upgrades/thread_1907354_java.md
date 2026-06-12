---
title: "java?"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by randywolf244 on 2012-01-11
so i tried to find java in my package management system and its nowhere to be found. does anyone know how to get it. im using xubuntu if it changes anything

---

### Post by KdotJ on 2012-01-11
When you say Java, do you mean the runtime or the development kit for programming in the Java language?

If the latter, you can install the JDK with:

```
sudo apt-get install openjdk-6-jdk
```

In fact, I think this includes the JRE.. but probably not the best way to install it if you're only after the runtime.

---

