---
title: "Jdk 6.0"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by zero-Tolerance on 2007-03-26
how can i install JDK 6.0 and then NetBeans

---

### Post by zvacet on 2007-03-27
If you have all repositories open you can find java in synaptic.Install it from there.

---

### Post by zdude on 2007-03-27
I don't think that jdk6.0 is in the repositories yet. I downloaded it from Sun's website that also included Netbeans 5.5 and from there executed the jdk-6...bin file and it installed the java 6.0 as well as the netbeans components, into their respective folders.  You need to add to your /etc/environment the path, Java_home and classpath settings (where the installer placed the files). If you are running Beryl, you need to set an additional environment  variable -  AWT_TOOLKIT="MToolkit" or you'll have a white screen in the netbeans IDE. it is a PITA to setup but it seemed to work ok once you've jumped through these hoops. Good luck. Also, if you've installed the 1.42 JDK or runtime, you need to remove them or you may have conflicts with the jdk 6.0 - esp. pathing problems.

---

### Post by tomservo291 on 2007-03-27
If you're doing Java development or anything, never let the OS manage your Java VM's...

Ubuntu ships with some weird thing by default, never even heard of it before (gjt VM or something?)  

If you want to use Eclipse, NetBeans ant and manual invocation of compilers and java binaries (as would most people that do Java dev,) you will constantly need to switch what VM/JDK you are using.  I.E. NetBeans needs to run in 1.6.0, but I need it to compile with 1.4.2.  But the project I build for company x uses J2SE 1.5.0, so my ant build task needs to use the 1.5 JDK.  

You will have one hell of a time managing this letting Ubuntu manage your JVM's.

Easiest solution:

Install all the JDK's somewhere, for example:

/home/alex/java/j2sdk1.4.2_13
/home/alex/java/jdk1.5.0_11
/home/alex/java/jdk1.6.0

create the following symlinks:
ln -s /home/alex/java/j2sdk1.4.2_13 /home/alex/java/javahome
ln -s /home/alex/java/j2sdk1.4.2_13 /home/alex/java/javabin

Now, you have symlinks to java 1.4.2 ... what could this possibly do for you?
Edit your .bashrc or some other startup script where you set your env variables, set your JAVA_HOME to the /home/alex/java/javahome symlink, and put the javabin symlink at the beginning of your PATH.

Now you can write a simple shell script, i.e.:

#!/bin/bash

rm /home/alex/java/javahome
rm /home/alex/java/javabin
ln -s /home/alex/java/jdk1.5.0_11 /home/alex/java/javahome
ln -s /home/alex/java/jdk1.5.0_11/bin /home/alex/java/javabin

java -version


Create one of these for each jdk, and you can simply invoke a shell script to switch JDK's, and you will never have to manually change your JAVA_HOME and bin directory on the PATH.

---

### Post by zvacet on 2007-03-28
It is in the repository.If I can see it you have to be able to see it too.

---

### Post by zdude on 2007-03-29
I rechecked and yes, the JDK6.0 is in the repositories. I know it not was there a couple of weeks ago when I installed the jdk6.0 from sun, must have had a messed up sources.list. :confused:

---

