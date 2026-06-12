---
title: "Help with Netbean IDE and Java"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by gjianhui on 2008-10-14
I have install JDK 1.6 in ubuntu7 already. when i do a java - version, i get 

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
user1@cylaw-desktop:~/jdk/jdk1.6.0_07/bin$ 

javac -version
javac 1.6.0_07

But when i try to install netbeans, it show me this. So what shid I do?


user1@cylaw-desktop:~/jdk/jdk1.6.0_07/bin$ sh netbeans.sh
Configuring the installer...
Searching for JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 6 or JDK 5 is required for installing the NetBeans IDE. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.

To download the JDK, visit [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)
user1@cylaw-desktop:~/jdk/jdk1.6.0_07/bin$ 

many thanks

---

### Post by fballem on 2008-10-14
This is probably a really 'dumb' question, but the information that you provided is for the JRE. The JDK is different. Could you please start Synaptic and do a search for Sun Java. This will give you a list. Please check the list to make sure that BOTH the Sun Java JRE and the Sun Java JDK are installed, and that they're the same version.

I've attached a screen shot from my system that shows both Sun Java JDK and JRE are installed, and that they're both version 6. They are one above the other.

If the JDK is not installed, then select the one for the version of Java that you've installed (version 6, I believe) and install it.

Hope this helps,

---

