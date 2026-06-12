---
title: "Help installing Eclipse..."
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by hemajang on 2008-08-20
I'm trying to install, setup EclipseIDE in Ubuntu 8.04. I've been following some tutorials on how to do this. More specifically, trying to install Eclipse3.4. I get to the part:

Edit /etc/eclipse/java_home...
But I can't find it. I try...

sudo -b gedit /etc/eclipse/java_home

but it opens up a new blank file.

Steps taken so far in installation process:

1. Downloaded Eclipse 3.4
2. Extracted to folder in /home directory (according to one tutorial)
3. Ran sudo apt-get install eclipse sun-java6-jdk
4. Cannot edit /etc/eclipse/java_home (it's not there)

Any help would be appreciated

---

### Post by fballem on 2008-08-20
> **hemajang said:**
> I'm trying to install, setup EclipseIDE in Ubuntu 8.04. I've been following some tutorials on how to do this. More specifically, trying to install Eclipse3.4. I get to the part:

Edit /etc/eclipse/java_home...
But I can't find it. I try...

sudo -b gedit /etc/eclipse/java_home

but it opens up a new blank file.

Steps taken so far in installation process:

1. Downloaded Eclipse 3.4
2. Extracted to folder in /home directory (according to one tutorial)
3. Ran sudo apt-get install eclipse sun-java6-jdk
4. Cannot edit /etc/eclipse/java_home (it's not there)

Any help would be appreciated

I found the following link to be helpful:

[http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)

depending on whether you need Apache and Tomcat, you can ignore or use these.

You will also need to adjust the line that reads:

```
tar xzf wtp-all-in-one-sdk=1.0-linux-gtk.tar.gz
```

to use the actual filename that you downloaded from the Eclipse site.

---

### Post by manishtech on 2008-08-20
I am also using 8.04 and installed eclipse just 12 hrs back. I just did a
[INDENT][FONT=Verdana][SIZE=4][COLOR=DarkOrange]sudo apt-get install eclipse[/COLOR][/SIZE][/FONT]
[/INDENT]
and it downloaded 101MB of packages including dependencies like eclipse, JRE,JDK or more... It automatically set up everything, even JAVA_PATH and everything is working fine.

BTW here is the content of my /etc/eclipse/java_home

> # This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

#/usr/lib/jvm/java-7-icedtea
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.6-sun
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun


---

### Post by fballem on 2008-08-20
> **manishtech said:**
> I am also using 8.04 and installed eclipse just 12 hrs back. I just did a
[INDENT][FONT=Verdana][SIZE=4][COLOR=DarkOrange]sudo apt-get install eclipse[/COLOR][/SIZE][/FONT]
[/INDENT]
and it downloaded 101MB of packages including dependencies like eclipse, JRE,JDK or more... It automatically set up everything, even JAVA_PATH and everything is working fine.

BTW here is the content of my /etc/eclipse/java_home

You may want to check the version number of Eclipse. If I recall correctly, the version that is in the repositories is version 3.2. Eclipse is up to version 3.4. The method that was outlined in the link will allow for the installation of eclipse 3.4. Also, the version that is in the repository uses Open Java. The link includes instructions for installing the Sun Java SDK.

To the best of my knowledge, if you want to upgrade, you will need to uninstall the version from the repository (I use Synaptic). Select remove all, which will uninstall any configuration files.

Regards

---

### Post by manishtech on 2008-08-21
Yeah! Its 3.2, but I always preferred the packages in the repository more than compiling from source or getting from download site and installing it manually.

---

### Post by fballem on 2008-08-21
As a general rule, so do I. There have been two exceptions since I converted to ubuntu in May:

Eclipse and hplip. Eclipse because I wanted to use the modeling tools, which were first used in 3.3 and are farther along in 3.4 and hplip because the repository version does not support my printer, but the current version does.

---

