---
title: "Cannot Install IntelliJ IDEA"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by kikkertje on 2008-06-08
Hi,

I downloaded and untarred the Idea-7.0.3 archive, 
but when I try to run ~/Desktop/Idea7757/bin/idea.sh
i get the following error:

```
ERROR: cannot start IntelliJ IDEA.
No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
exec: 61: /bin/java: not found

```

I have the package sun-java6-jdk installed though!

thanks in advance

---

### Post by Partyboi2 on 2008-06-08
See [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=600878") thread

---

### Post by kikkertje on 2008-06-08
I have tried the steps from the other thread

my /etc/environment looks like this:

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun/jre/bin/java"
LANG="en_US.UTF-8"
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06:."
CLASSPATH="/usr/lib/jvm/java-6-sun-1.6.0.06/bin:."
JDK_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06/"

```

and I still receive the error

---

### Post by Partyboi2 on 2008-06-08
I played around with it and was able to install it by
```
 export JDK_HOME=/usr/lib/jvm/java-6-openjdk
```
then run
```
sh idea.sh
``` again

---

