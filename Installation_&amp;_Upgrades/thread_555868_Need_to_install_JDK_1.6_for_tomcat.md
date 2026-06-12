---
title: "Need to install JDK 1.6 for tomcat"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by iangregson on 2007-09-20
Hi there,

I was following this guide to install tomcat 6... got past the first bit :) .. installing tomcat.. but i need to installed java JDK 1.6 [http://ubuntuforums.org/showthread.php?t=420034&highlight=tomcat6](http://ubuntuforums.org/showthread.php?t=420034&highlight=tomcat6)

I can't seem to locate it in Synaptic or ADD/remove ... 

In the link above, it tells me to download tomcat from apache which i did and installed without fail but then it says get the latest JDK which i believe is 1.6 .. but doesn't say where...

Any ideas?

Thanks in advance

Ian

---

### Post by sgordon on 2007-10-02
Hi there.

First, apps often say, 'get the latest java'. In this case, Tomcat 6 only needs Java 1.5 (aka. Java 5).

See the readme at:

[http://mirror.fubra.com/ftp.apache.org/tomcat/tomcat-6/v6.0.14/README.html](http://mirror.fubra.com/ftp.apache.org/tomcat/tomcat-6/v6.0.14/README.html)

Although I think JDK 1.6 is in the repositories (multiverse), hm. Anyway, the package you want, is:
sun-java6-jdk
or
sun-java5-jdk

(from memory, go for Java 6 if you aren't sure. Search for 'jdk' if I haven't got those right)

Also run:
sudo update-java-alternatives -s java-6-sun
or
sudo update-java-alternatives -s java-1.5.0-sun

Which will make the installed version the default JRE/JDK for your setup.

I'll try it out tonight for myself. Anyhow, see how it goes.

  Si

---

