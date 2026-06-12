---
title: "problem running eclipse on ubuntu"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by sam_barker123 on 2008-08-16
Hi everyone,
I am trying to run eclipse on Ubuntu.But it crashes with an error 
Error creating the view.
org.eclipse.core.runtime.Plugin 

Does anyone know how to fix it.
I did edit /etc/eclipse/java_home and moved the gcj entry..but it does not seem to help

---

### Post by ad_267 on 2008-08-17
This might help: [http://ubuntuforums.org/showthread.php?t=606006](http://ubuntuforums.org/showthread.php?t=606006)

Sounds like you need sun java.
```
sudo apt-get install sun-java6-jre sun-java6-bin
```

---

### Post by tinny on 2008-08-17
> **ad_267 said:**
> This might help: [http://ubuntuforums.org/showthread.php?t=606006](http://ubuntuforums.org/showthread.php?t=606006)

Sounds like you need sun java.
```
sudo apt-get install sun-java6-jre sun-java6-bin
```

If the OP is using a 32 bit Ubuntu install they should completely switch to Sun Java 6.

```

sudo apt-get update
sudo apt-get install sun-java6*

```

This will install JRE, Java browser plug-in and the Sun JDK.

You should make sure that you are compiling using the Sun JDK compiler.

In “Window” > “Preferences” > “Installed JREs” you need to “Add” the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.

---

### Post by pcjunkie on 2008-08-19
You might need to tell Ubuntu which java library to use.

---

### Post by tinny on 2008-08-19
> **pcjunkie said:**
> You might need to tell Ubuntu which java library to use.

Done like this

```

sudo update-alternatives --config java

```

---

