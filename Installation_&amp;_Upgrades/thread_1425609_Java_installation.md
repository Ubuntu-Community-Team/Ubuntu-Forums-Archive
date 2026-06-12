---
title: "Java installation"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by unueco on 2010-03-09
After my initial install of ubuntu, i installed the additional package that listed providing support for various misc things like allow mp4 videos to be played, etc. One of the items is supposedly JAVA.....but I can't seem to find it!!

I tried using a "find" command to locate it...or some components...no luck (but I am not confident I issued the command correctly)

So the question is: how/where is Java installed? How do I "get" to it?

---

### Post by doas777 on 2010-03-09
here are instructions for installing sun java:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
(be sure to use the update-alternative line if you install the sun version).

to find it, just open a terminal and run :
```

karmic:~$ which java
/usr/bin/java
karmic:~$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2009-11-05 10:53 /usr/bin/java -> /etc/alternatives/java
karmic:~$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 40 2009-11-05 10:53 /etc/alternatives/java -> /usr/lib/jvm/java-6-openjdk/jre/bin/java

```

so now I can tell that the java that my system uses by default is the openjdk v6, located at /usr/lib/jvm/java-6-openjdk/jre/bin/java

hth

---

