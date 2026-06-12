---
title: "Installing Oracle JDK on Xubuntu64 11.10 crashes"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by sejens on 2012-01-09
Hi!

I'm trying to install the Java JDK with Netbeans on XUbuntu64 11.10.

I've got the file  jdk-7u2-nb-7_1-linux-ml.sh from [http://www.oracle.com/technetwork/java/javase/downloads/jdk-7-netbeans-download-432126.html ]("http://www.oracle.com/technetwork/java/javase/downloads/jdk-7-netbeans-download-432126.html")and I try to install it like this:

> 
jens@acer13:~/Hämtningar$ ls jdk*
jdk-7u1-nb-7_0_1-linux-ml.sh  jdk-7u2-nb-7_1-linux-ml.sh
jens@acer13:~/Hämtningar$ sudo ./jdk-7u2-nb-7_1-linux-ml.sh
[sudo] password for jens: 
Configuring the installer...
Searching for JVM on the system...
Preparing bundled JVM ...
Extracting installation data...
Running the installer wizard...

Exception: java.lang.NoClassDefFoundError thrown from the UncaughtExceptionHandler in thread "main"
jens@acer13:~/Hämtningar$ ^C
jens@acer13:~/Hämtningar$ 
This worked when I ran XUbuntu32 11.10. However in order to be able to use the [OPA programming]("http://opalang.org/faq.xmlt") language I needed to switch to 64 bit. However, I still want to be able to program in Java...

Any ideas why the installation of the JRE crashes?

Thanks
Jens

---

### Post by KdotJ on 2012-01-09
You can install the open JDK straight from the Ubuntu repos, by typing the following into a terminal:

```
sudo apt-get install openjdk-7-jdk
```

That's assuming that you want Java 7, if not replace the 7 with a 6 in the command. Similarly, Netbeans is also available from the repos, and you can find it in the software centre

---

### Post by sejens on 2012-01-09
Thanks.

Will that give me Netbeans too? And what's the difference between open JDK and Oracle JDK?

I'm very tempted by this bundle since I worked in that environment before (Oracle JDK + NetBeans).

/Jens

---

### Post by KdotJ on 2012-01-09
Yeah netbeans is easily available too... to install it all in one lump, type the following into a terminal:

```
sudo apt-get install openjdk-7-jdk netbeans
```

The Open JDK differs from the Oracle one by the fact it is open-source (the source code is freely available). I believe that Oracle are moving toward the openJDK anyway (someone correct me if I'm wrong), check out [this wikipedia page]("http://en.wikipedia.org/wiki/OpenJDK") for more info if you're interested.

---

