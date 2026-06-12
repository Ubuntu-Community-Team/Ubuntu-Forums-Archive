---
title: "Java install"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by sinbowden on 2011-12-19
Problem: 

terminal command: sudo apt-get install sun-java6-jdk sun-java6-jre 
terminal responds: E: Package 'sun-java6-jre' has no installation candidate

any Idea?

---

### Post by d2btoo on 2011-12-19
Probably because of this...

[http://www.h-online.com/security/news/item/Canonical-to-remove-Oracle-s-Sun-Java-from-users-systems-1396528.html](http://www.h-online.com/security/news/item/Canonical-to-remove-Oracle-s-Sun-Java-from-users-systems-1396528.html)

[https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html)

---

### Post by sinbowden on 2011-12-19
Thank you :)

---

### Post by d2btoo on 2011-12-19
Yea, options are OpenJDK and/or Oracle java (aka java 7) ... more info here... [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by sinbowden on 2011-12-19
i read the links and installed openjdk-6-jdk and openjdk-6-jre and i get this msg when i try to execute a .sh:
 if ! java -version > /dev/null 2>&1
then
echo "Could not find Java."
echo "You must have Java installed and in your path."
exit
fi

relativePathToGame=`dirname $0`
cd $relativePathToGame


java -Xmx512m -cp bin/patch.jar:bin/triplea.jar games.strategy.engine.framework.GameRunner

do you have any ideas?

---

### Post by d2btoo on 2011-12-20
Hi,
I don't use OpenJDK so presently I don't have java (sun, oracle) installed in my linux partion... this means if I tell you to do some troubleshooting steps it's going to be guess-work, so I think it will be better to wait for somebody actually running OpenJDK, who can guide you more properly. Sorry.

BTW you did UN-install Sun java before migrating to OpenJDK, right? if not  probably Sun is still default!?? .... just a hunch...

EDIT: you seem to have posted this on here [http://kubuntuforums.net/forums/index.php?topic=3119768](http://kubuntuforums.net/forums/index.php?topic=3119768) also, well good luck there, I'm out!

---

### Post by cybergalvez on 2011-12-20
> **sinbowden said:**
> Problem: 

terminal command: sudo apt-get install sun-java6-jdk sun-java6-jre 
terminal responds: E: Package 'sun-java6-jre' has no installation candidate

any Idea?

I basically followed the advice on this link [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html) and just installed oracle java 7 so far it works great

---

