---
title: "How ti install JDeveloper"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by MickSulley on 2007-12-09
Hi,
I have installed Oracle 10g (after many problems) and I now want to install JDeveloper.  I have downloaded it (Oracle JDeveloper 10g 9.0.5) but when I try to run it I get the message 

Type the full pathname of a J2SE installation (or Ctrl-C to quit), the path will be stored in ~/.jdev_jdk?

I have installed various java packages but when I enter the path to them I get 

Error: Java home /usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/java is not a J2SE SDK.
Running Oracle9i JDeveloper under a JRE is not supported.

If the Java VM specified by the SetJavaHome is actually a full J2SDK installation
then add 'SetSkipJ2SDKCheck true' to the jdev.conf configuration file


Can someone tell me which file I should be downloading from Sun and how to get JDeveloper to work?

This is most frustrating because I have downloaded the same JDeveloper file in windows and it just runs

I am new to Linux and to Java, so please keep the explanations simple!

Thanks

Mick

---

### Post by esmin on 2007-12-13
you need to install JDK (Java Development Kit) to run JDeveloper, that is you need JDK to develop java applications.

You already have JRE (Java Run-time Engine) which is required for running java apps.

JDK installation includes JRE.

when you install JDK, point JDeveloper to JDK folder, and I think it should work...

---

### Post by stonkie on 2008-02-08
I have followed the exact path as MickSulley and successfully ran Jdeveloper in command line. It now asks me to point it to the Jdk, but I installed the jdk using synaptic and I have no idea where it went... Where could it be installed? Even a search didn't find it...

There is a directory in /usr/lib/jvm/java-6-sun-1.6.0.03/jre which seems to contain the structure Jdeveloper expects but it complains that it is a jre instead of a jdk (when I point it there, I get another error message saying I can bypass the verification by editing the configuration files which is not what I want)... 

I could previously download the Jdk directly from Sun and run jdeveloper, but my linux crashed and I had to reinstall. I would like to keep the machine as clean as possible by using the synaptic whenever possible this time... There just has to be a location on the filesystem where it got installed! Or maybe a repository with Jdeveloper in it?

---

### Post by Matt Ball on 2008-02-14
Try /usr/lib/jvm/java-6-sun/

Which worked for me. It will then complain about not being certified for Java 1.6

If you have desktop effects turned on you may get a blank window. If you do turn of the desktop effects off.

---

