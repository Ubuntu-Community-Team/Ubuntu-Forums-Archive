---
title: "Question regarding installing of latest SUN JDK"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by dejanh on 2007-01-09
Hi all,

I've done a search of the forums but nobody seems to explain how to install and configure the latest JDK from SUN on Ubuntu 6.06+.  I already know how to install the apt-get version of JDK but that one is 1.5 update 6 and I want to be able to install and configure 1.5 update 9 and higher from SUN's download.

Could anybody clue me in on how to install it properly?  I have Java 6 installed right now in /opt/SDK/jdk which is being used by NetBeans fine, but I want to be able to also set this as the default system JVM (i.e. I want java and javac to be version 6 not 1.5 update 6, and all other programs that use Java to default to this installation).

Thanks a lot in advance!

---

### Post by :mo on 2007-01-09
you could download the rpm, convert it into a .deb using alien and then install it via ```
dpkg  -i *packagename.deb*
```

---

### Post by dejanh on 2007-01-09
Ok, I think I overcomplicated my own question.  I do not have a problem installing the binary.  Hence why I said that I already have Java 6 installed in /opt/SDK/jdk.  However, what I need is the "rest" of the installation.  The "how-to configure JDK to be the default JDK on the system" part :)

If I just set all the path variables and stuff it does not work still as the default system Java installation always overrides it...

I need a way of permanently linking this thing to be "the" Java installation for the system...

Any ideas?

---

### Post by areks on 2007-01-10
You can try this. However this may break something, so pleas do it on your own responsibility.

Go to:
```
cd /etc/alternatives/
```

This is only to make copy in case you will need to revers it one day.
```
sudo mv java java_gcj
sudo mv jar jar_gcj
```

and do this (but replace path according to yours system):
```
sudo ln -s /opt/java/jdk6_0/jdk1.6.0/bin/java
sudo ln -s /opt/java/jdk6_0/jdk1.6.0/bin/jar
```

test it with:
```
java -version
```

There are also java.1.gz and jar.1.gz links in this folder. I have no idea what this can be,  how it should be changed and for what this is used.

I also believe Sun Java 6 should be in standard repository and default or at last alternative  Java in system science it is now GPL.

Good luck.
Arek

---

### Post by GSMD on 2007-01-13
A good explanation with in-depth details on JDK6 installation is [here](http://www.centricware.org/confluence/display/~alex.yanchenko/Installing+JDK6+on+Debian+Etch+%28or+Ubuntu%29).

---

### Post by TwistedAnimator on 2007-01-15
> **GSMD said:**
> A good explanation with in-depth details on JDK6 installation is [here](http://www.centricware.org/confluence/display/~alex.yanchenko/Installing+JDK6+on+Debian+Etch+%28or+Ubuntu%29).

Thank you for that link! Worked perfectly for me.

---

### Post by dejanh on 2007-01-17
Awesome link :)  Thanks a lot! :D

---

