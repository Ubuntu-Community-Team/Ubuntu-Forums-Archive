---
title: "firefox 1.0.6"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by simple on 2005-07-21
like two months back when i installed ubuntu, i followed ubuntuguide.org to setup java.. i had some problem updating firefox, but got that done.. now i can't get java running on it. thought maybe it was java, so i used synaptic to "uninstall" sun-jsre2 or whatever, to reinstall, it doesn't seem to be apart of the repository anymore... > simple@elemental:~$ java -version
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)
simple@elemental:~$ i'm getting that still, when doing java version. so i guess it didn't uninstall, how can i get it working with firefox again? > simple@elemental:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate
simple@elemental:~$ that's the error for trying to get it again

---

### Post by simple on 2005-07-22
all i did was found the firefox java plugin firefox-java-plugin.so and copied to the plugins folder of the install folder.. thanks for reading this? i guess, or thanks for something

---

