---
title: "Can't install Sun Java 6 JDK"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by lipinski on 2009-11-30
I recently upgraded from 9.04 to 9.10.

After the upgrade, I installed Eclipse via Synaptic.
Now, I'm trying to install the Sun Java JDK, and I cannot because of a dependency problem:

sun-java6-jdk:
  Depends: sun-java6-bin (=6-15-1) but 6-16-0ubuntu1.9.04 is to be installed

I tried uninstalling sub-java6-bin and sun-java6-jre, but I cannot do that because Synaptic wants to then uninstall Eclipse.  

Any ideas how to get around this?
Secondly, do I even need JRE if I install JDK?

---

### Post by jamesstansell on 2009-11-30
The JDK package needs the -bin and -jre packages to work, I'm pretty sure.  Note that eclipse generally will work without the JDK package but I'm not familiar with recent eclipse packaging in ubuntu.

I'm also not running 9.10 yet so I can't try to reproduce your situation.

To get around the mis-matched versions you should be able to tell synaptic (or aptitude or apt-get or etc) exactly which version of which package you want.  But I haven't had to worry about that for a long time.

Hope that helps at least a little bit.

---

### Post by jamesstansell on 2009-12-01
Also, just wondering if you really need the sun-java6 jdk.  The openjdk6 jdk may actually be better in general.

Sadly, for the browser plugin, the sun one is still generally preferable.  But it doesn't need a jdk, and can easily co-exist with the openjdk packages.

---

### Post by insanity54 on 2009-12-01
I can reproduce this error. I get the exact same error message as lipinski.

I also recently upgraded from 9.04 to 9.10.

---

### Post by lipinski on 2009-12-02
I got through it.  It wasn't pretty as I had to remove the -bin and -jre packages, which in turn removed all the dependencies (most importantly eclipse packages).  I then re-installed the -jdk, -jre, -bin, and eclipse packages (using the lower versions for java packages).

That resolved my problem.  However, I didn't have anything setup in eclipse yet, so I don't know how that would impact someone that has eclipse set up just right as far as configuration settings, projects, etc.  Hopefully you wouldn't lose your work, but be cautious...

---

### Post by brimbleshoes on 2009-12-08
The above solution worked for me.  Thanks for the help!

I had to remove the ubuntu 9.04 sun java 6 packages.  Then I was able to install the 9.10 sun java 6 packages.

Makes sense now ... I was trying to apply the JDK package for 9.10 to a JRE package that was marked for 9.04.

---

### Post by athrpf on 2009-12-19
I have the same problem.

It does make sense that you need to upgrade to the 9.10 packages, but why isn't that done automatically? Shouldn't that be considered a bug?

---

### Post by montego95 on 2010-01-05
In my opinion it absolutely should be considered a bug.  If I uninstall these other packages, Synaptic will uninstall about 20 other applications that I am using, including Open Office 3.1, which is totally unacceptable.  Folks really need the option to "upgrade" to the JDK version of Java 6 running in Karmic without having to lose all these apps and having to re-install and configure all of these...  JMO though.  Very frustrating...  will probably force me to use VirtualBox and run a separate guest Ubuntu OS for my venturing into Java development for the Android.  Not ideal for sure.

---

### Post by Wardje on 2010-02-13
Using
```
sudo aptitude install sun-java6-jdk
```
seemed to be the easiest solution for me as opposed to removing everything.

---

### Post by ziroby on 2010-04-08
The problem is that it's depending on an old version of the JRE.  So we need to downgrade the JRE to 6-15-1.  Use apt-get install, specifying explicit version numbers:
```
sudo apt-get install  sun-java6-jre=6-15-1 sun-java6-bin=6-15-1
```Then you can do a regular installation of the JDK:
```
sudo apt-get install  sun-java6-jdk
```That seemed to work for me.

---

