---
title: "gcc-3.4"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by bodiebot on 2006-11-21
Please help!!! :D I'm an absolute newby to a COMPUTER!. I have recently installed ubuntu in it. But I have an ADSL modem that needs a special pakage to be installed (ueagle-atm.) In order to install the package I need to install first the gcc-3.4 which is not included in my ubuntu version. How can I download the gcc-3.4 package and install it?

---

### Post by taurus on 2006-11-21
System -> Administration -> Synaptic Package Manager.  In the Search field, type "gcc-3.4" and highlight it to install it!  

Are you sure you need gcc-3.4 or any version of gcc would do?  Another way is, Terminal -> Accessories -> Terminal

```
sudo aptitude update
sudo aptitude install build-essential
```
Or you can install "build-essential" from synaptic as well.

---

### Post by jagguars on 2006-11-24
ah okay, i know that ;)
try
```

sudo apt-get update
sudo apt-get install gcc-3.4

```
if that doesn't work go to adept (start>system>adept) go to fetch updates and then search for gcc. klick the 3.4 version. if u have a preinstalled other version. to find out do: gcc -v you got to install the 3.4 as well and then do this: [http://ubuntuforums.org/showthread.php?t=299192&highlight=gcc+3.4]("http://ubuntuforums.org/showthread.php?t=299192&highlight=gcc+3.4") in a short do:
```

./configure CC=gcc-3.4

```

---

