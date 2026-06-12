---
title: "Fixing Java 8 installation attempt (or going back to java 7)"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by Eric_Darsow on 2014-12-13
Hi folks. I made a mess and I'm hoping you can help me fix it. I made the cardinal error of being new to Ubuntu and following a posting for installing Java 8 and i typed in commands that I only had a rough idea of what they were doing. I'm running Xubuntu 14.04. I know now that the system has java 7 running on it. And yet I am taking an intro Java class and was told to install the most current version of JDK from oracle, which is Java 8. 
I run Java -version and get this.
```

java version "1.7.0_65"
OpenJDK Runtime Environment (IcedTea 2.5.3) (7u71-2.5.3-0ubuntu0.14.04.1)
OpenJDK 64-Bit Server VM (build 24.65-b04, mixed mode)

```

So I went online and tried to follow instructions for installing Java 8 JDK that was made for a "general linux" box. 
The problem is that the command that I thought was supposed to unpack the tarball and put it into /opt/jdk didn't work. 
tar -zxf jdk-8u5-linux-x64.tar.gz -C /opt/jdk

I got this output:

```

tar (child): jdk-8u25-linux-x64.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```

I tried to work around the tar problem by extracting the tar ball in thunar using right clicking and then moving the unpacked folder to /opt/jdk/jdk1.8.0_25/ which is where it is now sitting.

Thinking I had an unpacked java 8 JDK in the right folder according to the online instructions, I ran these updates to point the system to a java that doesn't seem to be working correctly:
```

  update-alternatives --install /usr/bin/java java /opt/jdk/jdk1.8.0_05/bin/java 100

update-alternatives --install /usr/bin/javac javac /opt/jdk/jdk1.8.0_05/bin/javac 100

```
I know I screwed things up because I can compile a basic hello world java app to test the system but I get this error when I run the command: java HelloWorldApp

```

Exception in thread "main" java.lang.UnsupportedClassVersionError: HelloWorldApp : Unsupported major.minor version 52.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:800)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:449)
    at java.net.URLClassLoader.access$100(URLClassLoader.java:71)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:361)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:425)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:308)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:358)
    at sun.launcher.LauncherHelper.checkAndLoadMain(LauncherHelper.java:482)

```

I think something got pointed wrong since this is the output I get when I run update-alternatives --display javaThat third line seems to be pointing to a java 8 that isn't installed. 

```

java - auto mode
  link currently points to /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
/opt/jdk/jdk1.8.0_25/bin/java - priority 100
/usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java - priority 1071
  slave java.1.gz: /usr/lib/jvm/java-7-openjdk-amd64/jre/man/man1/java.1.gz
Current 'best' version is '/usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java'.

```


Can you help me fix this, I'm sorry for being a newbie whose doing stuff beyond my skill level. I've learned my lesson. I don't know if it's easier to get the Java 8 JDK working or to go back to pointing everything to java 7 jdk. Either one is fine with me--I just need to be able to compile and run very basic java code. Thanks!

---

### Post by QIII on 2014-12-13
Hello!

Would you please point out the instructions you used so we can see what condition your machine might be in?

Once we figure that out, I will point you towards the very easiest methods of installing Java 8.

OpenJDK can be installed easily from the repositories and Oracle Java 8 can be installed easily with just three commands in the terminal.

---

### Post by Eric_Darsow on 2014-12-13
Hi, 

The instructions were at
[https://www.digitalocean.com/community/tutorials/how-to-manually-install-oracle-java-on-a-debian-or-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-manually-install-oracle-java-on-a-debian-or-ubuntu-vps)

---

### Post by QIII on 2014-12-13
Unfortunately, you have found a set of instructions that are **far, far** more complicated than they need to be.  

It's not even that complicated for Fedora.

I'm often not sure if those who produce such instructions are interested in helping out as much as showing off.

For Ubuntu, please see [this]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"), which I also reference in the Java link in my signature.

Judging from those instructions, you should be able to clear this up using webupd8.

As opposed to the method you used, the webupd8 method will keep Oracle Java updated as Oracle releases updates.  The other method requires reinstallation with every newly released update.  Andrew at webupd8 has automated the entire process of downloading, installing and setting up the browser plugin.  His scripts are updated as new updates are released and your installation is updated within a few hours.

---

### Post by Eric_Darsow on 2014-12-13
You, sir, are sent from the gods. Worked like a charm. I'm very grateful.

---

