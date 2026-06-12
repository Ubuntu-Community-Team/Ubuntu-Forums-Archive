---
title: "installing jdk 6 from computer"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by jahin on 2009-12-13
hi
im using ubuntu 9.04
recently i downloaded jdk6_13.bin file and when i tried to install this t faced some problems. the process i tried is
make a directory *"java"* in */usr*
then paste the jdk.bin file and used *sudo ./jdk.bin*
and it was shown that it is installed but when in terminal i typed **java** or **java -version**
its showing that java is not installed
moreover i added the lines at */etc/profile*

[B]export JAVA_HOME=/usr/java/jdk1.6.0_13/bin/java
export PATH=$PATH:$JAVA_HOME/bin


[/B]but its not working.
plz anyone help me to do this.
thanks for the help.

---

### Post by phillw on 2009-12-13
I put java on a while back - and can't for the life of me remember the tutorial i followed !!!

This one seems a good guide.

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/#comments](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/#comments)

Putting a TomCat Java server on can be done by issuing the command

```
 sudo tasksel
```  and selecting the Java server (arrow up / down, press space to mark the choice - then hit enter)

Hope that helps.

Regards,

Phill.

---

### Post by jahin on 2009-12-13
probably this is the best [link]("http://ubuntuforums.org/showthread.php?t=1113039")
any way thanks for the reply

---

### Post by phillw on 2009-12-13
> **jahin said:**
> probably this is the best [link]("http://ubuntuforums.org/showthread.php?t=1113039")
any way thanks for the reply


Kewl link. The how-to i did was for programming mobile phone apps - It lurks on the forum somewhere !!!

Phill.

---

### Post by jamesstansell on 2009-12-15
sun-java6 u17 fixed some security problems in u15 which fixed security problems in u13 which makes u17 preferable in general.

It's too bad that the sun-java6 packages are currently unmaintained.  Which suggests to use openjdk if that was sufficient but that's a whole other topic.

Regards,

-james.

---

