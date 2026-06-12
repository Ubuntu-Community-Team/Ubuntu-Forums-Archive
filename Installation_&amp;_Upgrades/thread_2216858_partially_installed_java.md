---
title: "partially installed java"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by Riunixteam on 2014-04-14
Hi,

We have done manual upgrade from JAVA 1.6 to JAVA 1.7 version with below steps:
**sudo add-apt-repository ppa:webupd8team/java**
**sudo aptitude update**
**sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/java-7-oracle/bin/java" 1**
**sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/java-7-oracle/bin/javac" 1**
**sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/java-7-oracle/bin/javaws" 1**
**sudo update-alternatives --set java /usr/lib/jvm/java-7-oracle/bin/java**
**sudo update-alternatives --set javac /usr/lib/jvm/java-7-oracle/bin/javac**
**sudo update-alternatives --set javaws /usr/lib/jvm/java-7-oracle/bin/javaws**
 
I have then set “JAVA_HOME” in my application as “/usr/lib/jvm/java-7-oracle”
But now for routine software upgrades its giving me message like java is partially configured.
What can be the issue here?

---

### Post by slickymaster on 2014-04-14
> **Riunixteam said:**
> Hi,

We have done manual upgrade from JAVA 1.6 to JAVA 1.7 version with below steps:
**sudo add-apt-repository ppa:webupd8team/java**
**sudo aptitude update**
**sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/java-7-oracle/bin/java" 1**
**sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/java-7-oracle/bin/javac" 1**
**sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/java-7-oracle/bin/javaws" 1**
**sudo update-alternatives --set java /usr/lib/jvm/java-7-oracle/bin/java**
**sudo update-alternatives --set javac /usr/lib/jvm/java-7-oracle/bin/javac**
**sudo update-alternatives --set javaws /usr/lib/jvm/java-7-oracle/bin/javaws**
 
I have then set “JAVA_HOME” in my application as “/usr/lib/jvm/java-7-oracle”
But now for routine software upgrades its giving me message like java is partially configured.
What can be the issue here?

If those were the steps you used, you never got to install the WebUpd8 package. You went directly from updating your packages cache to the updating of the Java environment variables on your system.
After executing the **sudo aptitude update** command, you have to run the following:```
sudo aptitude install oracle-java7-installer
```

---

### Post by QIII on 2014-04-14
Just so you understand -- webupd8's PPA** *does not contain any Oracle Java binaries.***  They are not authorized to.

The installer downloads the binaries from Oracle and installs them.  If you do not use the included oracle-java7-installer, which scripts the download and installation, you haven't done anything.

I would be interested to know where you got instructions to do it as you attempted.

---

