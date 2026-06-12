---
title: "trying to install websphere"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by knowsgrace on 2008-04-12
I am trying to install websphere under UNBUNTU.   I keep getting the message

                                         Unable to locate an IBM or Sun SDK/JRE SE 5 in a well known location on your system.  If you have a recommended Java environment, re-invoke the launcher and explicitly specify the Java installation directory with the -is<colon>javahome option


What makes this perplexing is Eclipse runs fine.    Any suggestions?

---

### Post by glennoph on 2008-05-06
In the Synaptic Package Manager, search for sun-java, perhaps sun-java5-jdk.
Install the appropriate jdk.  You might have the adjust the java package to use as default.

--glenn

---

### Post by bobblehat on 2008-05-07
Yes - Eclipse seems to run fine with the default jdk.

To change to Sun Java 5 you can:

(do the install)
sudo apt-get install sun-java5-jdk

(set default java)
sudo update-java-alternatives -s java-1.5.0-sun

(confirm the version)
java -version

---

