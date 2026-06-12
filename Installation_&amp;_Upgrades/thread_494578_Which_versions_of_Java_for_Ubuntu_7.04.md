---
title: "Which versions of Java for Ubuntu 7.04"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2007-07-07
Just did another clean install in attempt to eliminate bonobo-activation error.  After initial load and updates, I went to [www.java.com](www.java.com) to get java rte.  Downloaded file (version 6 update 1) and installed per instructions.  Install appeared to go well, but verify section on java.com did not verify install.  Next used version 5 package in Synaptic to install.  This still did not verify on java.com, but did work with bellsouth.net dsl speed test.

So, what have I done wrong and what do I need to do to fix problem?

John

---

### Post by madmetal on 2007-07-08
open terminal and type
sudo aptitude search java   
or even better 
sudo aptitude search sun-java
and then see java packets that are on the repos..
you can install java-6 from the repos as well ;)
maybe you should uninstall what you have manually installed before..

---

### Post by CrankyFilipino on 2007-07-08
> **madmetal said:**
> open terminal and type
sudo aptitude search java   
or even better 
sudo aptitude search sun-java
and then see java packets that are on the repos..
you can install java-6 from the repos as well ;)
maybe you should uninstall what you have manually installed before..

Ok I did the sudo aptitude search and see all the packets here.. but I don't know what packet to install and how.. I'm still very noob lol

---

### Post by Damiel on 2007-07-08
Follow these instructions:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins)

then run in a terminal:
```
sudo update-java-alternatives -s java-6-sun
```

---

