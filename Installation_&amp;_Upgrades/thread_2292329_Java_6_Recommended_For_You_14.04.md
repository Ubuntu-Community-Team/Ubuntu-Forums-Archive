---
title: "Java 6 Recommended For You 14.04"
date: 2015-08-27
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-08-27
Hello,

In Ubuntu Software Center OpenJDK Java 6 Runtime Environment is recommended for me. I've certainly noticed that I've been having some problems with apps that look and feel like Java problems. Also, Java 7 which comes with 14.04 out-of-the-box has been poorly reviewed. So, should I try Java 6? Can Java 6 be run in parallel with Java7; or do I have to remove Java 7, before or after installing Java 6? I really don't know how to proceed.

Any help appreciated.

Thanks, Hannibal

---

### Post by QIII on 2015-08-27
OpenJDK 6 and Oracle Java 6 are EOL and vulnerable.

If you want to install a version of Java, I recommend Oracle Java 8 -- and the easiest way to install it is to use [webupd8's script]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").  Andrew does a good job of keeping things up to date and you will get updates with your regular Ubuntu updates as Oracle releases them.

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

By way of explanation of the difference between OpenJDK and Oracle Java:

OpenJDK is open source.  But that doesn't mean it's disassociated from Oracle Java.  Oracle is the biggest mover and shaker in OpenJDK development.  They provide a team of engineers to work on it -- for good reason.  Oracle declared several years ago that OpenJDK would be the open source reference implementation of all things Java, including Oracle Java.  Sounds good, eh?  Well Oracle has most of the weight behind OpenJDK, so they can "gently guide" its development.  OpenJDK is more than just a tiny bit influenced by Oracle.  If you don't believe me, install the latest version of OpenJDK (Update 60 right now) and then go [here]("https://www.java.com/en/download/installed.jsp") to test your Java.  It'll say you have the latest version of Java.  Oracle Java.

So if you hear people say "I wouldn't use Oracle Java because OpenJDK is open source!  And I'd never have anything to do with Oracle." just smile.  They are under Oracle's sway.

---

### Post by coljohnhannibalsmith on 2015-08-27
[QUOTE=QIII;13345712]OpenJDK 6 and Oracle Java 6 are EOL and vulnerable.

If you want to install a version of Java, I recommend Oracle Java 8 -- and the easiest way to install it is to use [webupd8's script]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").  Andrew does a good job of keeping things up to date and you will get updates with your regular Ubuntu updates as Oracle releases them.

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

The test page stated that I had Java version 7-79; and instructed me to download and install the latest version. The install went smoothly and the the test page then reported that I had the latest version. I then checked Ubuntu Software Center and OpenJDK 7 is still installed. Should I, can I remove it?

Thanks, Hannibal

---

### Post by QIII on 2015-08-27
The two can live peaceably together on your machine.  One or the other has already been set as the one your system will use.

You can check by issuing the following command in the terminal:

```
java -version 
```

You got that message on the test site because OpenJDK 7 isn't the latest version.

---

### Post by monkeybrain20122 on 2015-08-27
Or use OpenjDk8 [https://launchpad.net/~malte.swart/+archive/ubuntu/openjdk8](https://launchpad.net/~malte.swart/+archive/ubuntu/openjdk8)
I seemed to have problems setting up Java_Home path with Oracle Java for some applications. On the other hand I don't see any necessity or advantage in using Oracle java unless you use the few applications that explicitly require it (mostly Oracle stuffs like Netbeans)

---

