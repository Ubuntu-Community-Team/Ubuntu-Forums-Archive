---
title: "Installing Java"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by factorof2 on 2005-07-23
I recently got the Java SDK/JRE stuff to install in Ubuntu.  I converted the RPM to a DEB just fine and extracted all the files.  However, when I run Java dependent applications I get an error that the JVM couldn't be initialized because there's no instance of java/lang/Object.  I was just wondering if this had anything to do with setting classpaths or something similar such as in Windows.

---

### Post by adwait on 2005-07-23
Alien converts from RPM to DEB but doesn't always do a great job........I think you should try installing from a binary file.

---

### Post by maruchan on 2005-07-23
I had this happen with my java files...I had to do a bunch of stuff with the PATH settings or something like that, since it's possible that the command "java" is looking in the wrong area. Sorry I can't be of more help. 

One of the Java apps I use has a linux run script that checks several common JRE locations and finds the correct version, but unfortunately, not all developers offer scripts like this with their apps.

---

### Post by javiadip on 2005-07-24
[QUOTE=factorof2]I recently got the Java SDK/JRE stuff to install in Ubuntu.  I converted the RPM to a DEB just fine and extracted all the files.  However, when I run Java dependent applications I get an error that the JVM couldn't be initialized because there's no instance of java/lang/Object.  I was just wondering if this had anything to do with setting classpaths or something similar such as in Windows.[/QUOTE]

[http://wiki.ubuntu.com/Java](http://wiki.ubuntu.com/Java)

---

### Post by WildTangent on 2005-07-24
i think the solution at [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre) will be much easier for you, the wiki solution is quite complex

-Wild

---

### Post by factorof2 on 2005-07-24
Hm, well I think I found the problem.  I tried running some of the executeables that come with the Java package and none of my environment variables are set.  Does anyone know the list of environment variables, or could possibly paste a listing from the env command of variables related to Java.  I've searched Google and none of the sites I've seen have any variable lists.

---

