---
title: "32-bit Java on 64-bit Ubuntu 11.10"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by dtwood on 2011-10-11
I've download a java application that uses 32-bit libraries, and I've tried to install a 32-bit JRE by running
```
sudo apt-get install openjdk-6-jre:i386
```
However I'm getting an error message out saying:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 openjdk-6-jre:i386 : Depends: openjdk-6-jre-headless:i386 (>= 6b23~pre10-0ubuntu5) but it is not going to be installed
                      Depends: libgif4:i386 (>= 4.1.4) but it is not going to be installed
                      Depends: libxtst6:i386 but it is not going to be installed
                      Depends: libaccess-bridge-java-jni:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
I've tried to install libxtst6:i386 separately, however apt warns that a number of packages, including xorg. Is there any way of successfully installing 32-bit java on 64-bit ubuntu?

---

