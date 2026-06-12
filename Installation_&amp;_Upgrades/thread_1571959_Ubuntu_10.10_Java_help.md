---
title: "Ubuntu 10.10 Java help"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by 0xsergy on 2010-09-10
I've looked through previous threads but I cant find anything that matches my problem. I have all the OpenJDK files with all the openJRE files installed and even the icedtea java plugin but when i go and try to use java the window pops up to accept the program but after that it doesnt load. The java window stays black. Any certain file i have to install to fix this?

---

### Post by uRock on 2010-09-10
**sudo apt-get install ubuntu-restricted-extras** in a terminal will install all of the java stuff you need as well as Adobe Flash.

Why are you using 10.10? It is still in development.

---

### Post by nilarimogard on 2010-09-11
> **uRock said:**
> **sudo apt-get install ubuntu-restricted-extras** in a terminal will install all of the java stuff you need as well as Adobe Flash.

Why are you using 10.10? It is still in development.

That will install icedtea6-plugin for now as the Maverick partner repository doesn't have Java (don't know why...).

---

### Post by nilarimogard on 2010-09-11
OK, I just wrote a post on [installing Java in Ubuntu 10.10]("http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html")... hope that helps.

---

### Post by mhughes on 2010-11-27
Personally, in my little knowledge of Ubuntu, I installed the Sun Java packages (sun-java6-jre, sun-java6-plugin, sun-javadb-common) and then used the commands reported here [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java), in particular
```
sudo update-java-alternatives -l
sudo update-java-alternatives -s java-6-sun
sudo update-alternatives --config java
```to choose Sun Java as default java [FONT=Verdana](for me option number 2, see attachment)[/FONT].

Hope it helps.



p.s.: sorry for my english, I'm italian :)

---

