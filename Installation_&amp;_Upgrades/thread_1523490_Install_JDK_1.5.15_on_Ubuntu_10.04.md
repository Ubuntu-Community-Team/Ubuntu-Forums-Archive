---
title: "Install JDK 1.5.15 on Ubuntu 10.04"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by dbhatt on 2010-07-03
Hi,
I'm writing some code that I need to comply with the Java 1.5.15 libraries but I can't seem to be able to install JDK 1.5.15. I had JDK 6, which I uninstalled and then tried installing JDK 1.5, but now that I've extracted the binaries for JDK 1.5, my computer isn't able to find java. 

The which java command gives me nothing, while I can't run javac or java from the command line. Even going to the bin directory in the jdk folder followed by ./java and ./javac give me the following errors: 

$ ./java
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

I know there's a solved thread about this, but that thread suggests that I do the following: 
[http://wojox.homelinux.org/?p=78](http://wojox.homelinux.org/?p=78)

I tried, but this is what I got: 
he following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Could someone please help me out on this one? I've already spent an entire day on this. 

Thanks!

---

### Post by SmokeyThePanda on 2010-07-03
Check out the following link, it may help. 

[http://www.idroidproject.org/forum/viewtopic.php?f=24&t=194](http://www.idroidproject.org/forum/viewtopic.php?f=24&t=194)

---

### Post by SmokeyThePanda on 2010-07-03
Not 100% sure that's JDK, but it's the best I could find at present. If it isn't what you are looking for, I'll look some more. :p

---

### Post by dbhatt on 2010-07-07
Sorry, I forgot to reply. Yes, the link you posted got JDK 1.5 working on my Lucid install. 

Thanks!

---

