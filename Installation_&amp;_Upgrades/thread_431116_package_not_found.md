---
title: "package not found"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by noob12345 on 2007-05-02
can't install Java Runtime Environment

tried instructions on [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

but i got this:

owner@owner-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-jre
owner@owner-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-jre

Synaptic can't find any of the packages listed on the webpage listed earlier neither
i also searched on the ubuntu packages page, but it wasn't there




then I tried the instructions on [http://java.com/en/download/help/5000010500.xml#install](http://java.com/en/download/help/5000010500.xml#install)
but got this: 

owner@owner-desktop:/usr/bin$ chmod a+x jre-1_5_0-linux-i586.bin
chmod: cannot access `jre-1_5_0-linux-i586.bin': No such file or directory

when i clearly have the file on my desktop


PLEASE HELP 
Why aren't their any packages?

is there another way to install the java runtime environment

---

### Post by zvacet on 2007-05-02
**system>administration>software properties>chek all boxes>reload**

This will open all your repositories and after that go to thesynaptic and you will find java there.

---

### Post by noob12345 on 2007-05-05
I think I will stay in absolute begginner talk now

---

