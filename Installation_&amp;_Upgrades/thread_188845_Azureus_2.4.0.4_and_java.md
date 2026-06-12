---
title: "Azureus 2.4.0.4 and java"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by vumba on 2006-06-04
I have Azureus 2.4.0.4 and java version "1.5.0_06" with repositories

I have install azureus with this wizard : [here]("http://www.ubuntuforums.org/showthread.php?t=144546&highlight=azureus")

I have install Java 1.5 with repositories from: [here]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

and i have install java from: [here]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

My Java version is :

:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

and i have clicked it with command :

sudo update-alternatives --config java


There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
        1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:


This image which is in the site : [http://www.ubuntuforums.org/showthread.php?t=144546&page=3&highlight=azureus](http://www.ubuntuforums.org/showthread.php?t=144546&page=3&highlight=azureus)

When this image is on the screen and i press hide and it don't go away.

---

### Post by cyracks on 2006-06-04
I have the same problem and I think it started when I installed kde 3.5.3

---

### Post by vumba on 2006-06-04
I do not know i him I have in the Gnome from then that I put the Azureus

---

### Post by vumba on 2006-06-04
[QUOTE=cyracks]I have the same problem and I think it started when I installed kde 3.5.3[/QUOTE]
I do not know i him I have in the Gnome from then that I put the Azureus

---

### Post by psquared89 on 2006-06-04
The Azureus information window (the little thing that pops up) is a known bug that is yet to be fixed.  As of now, the only way to get rid of it is to restart azureus and make sure that you shut down azureus "properly" every time (manually exiting azureus before shutting down the pc).

---

