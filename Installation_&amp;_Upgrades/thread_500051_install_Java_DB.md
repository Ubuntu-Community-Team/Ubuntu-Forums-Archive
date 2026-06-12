---
title: "install Java DB"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Green on 2007-07-13
Hello Everyone-
I am a newbie for the linux world. I tried to install Java DB (kind of derby database) on ubuntu.  I extracted the bin file and don't know exactly where the ideal location for this installation.
Should I install it in opt, usr or some other directories?

Thx

---

### Post by zanglang on 2007-07-13
Java libraries usually go in /usr/share/java. Or, you could drop them into the JRE's lib directory (/usr/lib/jvm/java-6-sun/jre/lib/ext for Java 1.6), but it's probably not recommended.

---

### Post by Green on 2007-07-13
> **zanglang said:**
> Java libraries usually go in /usr/share/java. Or, you could drop them into the JRE's lib directory (/usr/lib/jvm/java-6-sun/jre/lib/ext for Java 1.6), but it's probably not recommended.

Thanks Zanglang-
Java DB like Derby database. For the Java database, do you recommend to install on /usr/share ?

Thx

---

### Post by zanglang on 2007-07-13
You mean copy the entire distribution folder and put it into /usr/share? That's doable... but you'd most likely only need the .jar files, right? Just copy the .jar files (most likely in a bin or lib directory) to /usr/share/java, and add that to your classpath if it's not there already.

By the way, is that this Java DB? [http://developers.sun.com/javadb/](http://developers.sun.com/javadb/)
If you have Java 6 installed the JDK should already come with it, so you wouldn't have to install it. :P

---

### Post by Green on 2007-07-13
> **zanglang said:**
> You mean copy the entire distribution folder and put it into /usr/share? That's doable... but you'd most likely only need the .jar files, right? Just copy the .jar files (most likely in a bin or lib directory) to /usr/share/java, and add that to your classpath if it's not there already.

By the way, is that this Java DB? [http://developers.sun.com/javadb/](http://developers.sun.com/javadb/)
If you have Java 6 installed the JDK should already come with it, so you wouldn't have to install it. :P

Thanks again,
Yup that is the exactly Java DB I want to use. Unfortunately I'm using NetBeans with Java 1.5. I've already put the Java DB in the /usr/share and my database instances in my home directory. 

It works perfectly for me, again thanks for your advice. :)

---

