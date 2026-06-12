---
title: "Installing 32-bit Java SDK on Ubuntu 9.10 Server"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by TheDelChop on 2009-12-02
Title says most of it, could anybody help me install the 32-bit versiof of the JDK in my x64 version of Ubuntu Server 9.10?

---

### Post by pi4r0n on 2009-12-02
I am not sure if [this]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html") is what you are looking for ??

---

### Post by TheDelChop on 2009-12-02
No, I can do this, my problem is I've got 64-bit Java on my 64-bit OS (Ubunutu Server 9.10  x64), but I'm trying to run an app that seems to need the 32-bit version.  I'm wondering if I can also install this on my server, and if so, where can I get the packages?

Thanks,

Joe

---

### Post by Groodles on 2009-12-02
I'm having the same problem.

x64 Ubuntu 9.10 Server install, running a 64Bit Java VM.

Cannot execute a particular .jar because it needs a 32Bit VM according to the error log.

```
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM

```

(This is the first Java app I've encountered this problem with, all my other Java apps work fine!)

---

### Post by TheDelChop on 2009-12-02
I've tried d/ling the jdk from sun, but when I run it I get the following error: 

```

jdk-6u17-linux-i586.bin: 477: ./install.sfx.7302: not found
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.

```

Is it possible I need some more 32-bit libs that I don't have installed?

---

### Post by TheDelChop on 2009-12-02
It does in fact seem that it was a dependency issue. I installed the 32-bit jre (sudo aptitude install ia32-sun-java6-bin) and that seemed to install the relevent libs I needed to then install the 32-bit java SDK.  Hope this helps.

Joe

---

### Post by uplink3r on 2010-01-19
I'm not exactly sure what the guy above me is saying, but the package for 32-bit java is "ia32-sun-java6-bin", but it will not install from the repository.

```

$ sudo apt-get install ia32-sun-java6-bin
...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-sun-java6-bin: Depends: sun-java6-jre (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

```

Sounds like it's only supported for 9.04. Can I compile 32-bit java for my computer?

---

### Post by bobbyallan on 2010-01-29
I found this link in a search for I have the same problem running 9.10 x64
[http://java.dzone.com/tips/32-bit-jdk-a-64-bit-ubuntu-sys]("http://java.dzone.com/tips/32-bit-jdk-a-64-bit-ubuntu-sys")
However im not initially sure how to follow the guide some help would be nice.

---

### Post by bobbyallan on 2010-01-29
I was able to install it with the method posted here

 [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/]("http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/")

However it would not run properly.

---

