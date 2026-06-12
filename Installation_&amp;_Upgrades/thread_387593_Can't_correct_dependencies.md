---
title: "Can't correct dependencies"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by gjallarhorn on 2007-03-18
I recently downloaded the package fontconfig-config_2.4.2-1ubuntu1_all.deb and tried to install it, but I had some weird error and it told me to enter 'sudo apt-get install -f' in terminal. When I did, I got the following:

Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1ubuntu1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Is there any way of fixing this problem? I've tried the synaptic, and everything it told me to, but I couldn't fix it since I'm a complete newb.

---

### Post by zvacet on 2007-03-18
synaptic>edit<fix broken packages

---

### Post by bapoumba on 2007-03-18
> **gjallarhorn said:**
> I recently downloaded the package fontconfig-config_2.4.2-1ubuntu1_all.deb and tried to install it, but I had some weird error and it told me to enter 'sudo apt-get install -f' in terminal. When I did, I got the following:

Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1ubuntu1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Is there any way of fixing this problem? I've tried the synaptic, and everything it told me to, but I couldn't fix it since I'm a complete newb.
Which version of ubuntu have you installed ?
2.4.2-1 is feisty version
2.3.2-7 is edgy version.

My guess is that you have edgy, and that you installed a .deb from feisty. Why ?

---

### Post by gjallarhorn on 2007-03-19
I've already tried the synaptic method zvacet told me to try, It still gives me this:

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Ah, I see now :(
So there's no way of fixing it now that I've messed it up :??

---

### Post by bapoumba on 2007-03-19
Yes, there is a way, but we have to know which ubuntu version you have installed.

---

### Post by gjallarhorn on 2007-03-20
I've got 6.10 (edgy) installed.

---

### Post by bapoumba on 2007-03-20
OK, please check this thread, you should be able to reinstall the edgy version, either with synaptic or dpkg ;)
[http://ubuntuforums.org/showthread.php?p=2022112]("http://ubuntuforums.org/showthread.php?p=2022112")

---

### Post by gjallarhorn on 2007-03-20
Thanks so much, the problem's fixed now :D

---

