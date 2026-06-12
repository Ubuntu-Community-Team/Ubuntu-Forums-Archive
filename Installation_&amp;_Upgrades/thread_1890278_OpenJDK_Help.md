---
title: "OpenJDK Help"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by stevanity on 2011-12-03
I installed ubuntu and I didnt notice OpenJDK 6 already installed. Then I installed openjdk 7 via apt-get. and then when I ran javac command I could compile stuff without problems. 

But then I ran java command but I get "UnsupportedClassVersionError"... 

My Java version: 
```

steve@ubuntu:~$ java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)
```

JAVA_HOME:

```
$ echo $JAVA_HOME
/usr/lib/jvm/java-7-openjdk-amd64
```

But when I do a **"whereis java"** I get pointed to **"/usr/bin/java" **which inturn points to **"/etc/alternatives/java"** which points to **"/usr/lib/jvm/java-6-openjdk/jre/bin/java"**

I tried setting the CLASSPATH to "/usr/lib/jvm/java-7-openjdk-amd64/lib" then I get the "ClassNotFoundException"

Please help me resolve this. I am also willing to purge all java outta my pc and re installing afresh if nothing works out.

---

### Post by stevanity on 2011-12-03
Thanks a lot for everyone for helping out! I cant thank you guyz enuff!

Anyway... this is how I sorted things out. 

I used the update-alernatives --configure java to set the default java as OpenJDK 7.

then I removed openjdk 6 completely and thus javac and rest of the development binaries were gone. 

But for some reason the jdk7 binaries were not registered. So I installed them manually using,

update-alternatives --install <link> <name> <path> <priority> 

Thus I got everything sorted out and javac -version gives java 1.7 correctly

Thanks again.

---

### Post by oldtimer7777 on 2011-12-03
Also here is another way to do what you wanted to do:

[https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

> **stevanity said:**
> Thanks a lot for everyone for helping out! I cant thank you guyz enuff!

Anyway... this is how I sorted things out. 

I used the update-alernatives --configure java to set the default java as OpenJDK 7.

then I removed openjdk 6 completely and thus javac and rest of the development binaries were gone. 

But for some reason the jdk7 binaries were not registered. So I installed them manually using,

update-alternatives --install <link> <name> <path> <priority> 

Thus I got everything sorted out and javac -version gives java 1.7 correctly

Thanks again.

---

