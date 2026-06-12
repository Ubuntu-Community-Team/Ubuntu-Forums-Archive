---
title: "Java Problems"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by Lee2010 on 2009-12-20
I recently tried to follow this tutorial

[http://www.ubuntugeek.com/install-java-runtime-environment-jre-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-java-runtime-environment-jre-in-ubuntu-9-10-karmic.html)

on how to update my java but when I got to the "Sun Operating System Distributor License for Java" it wouldn't let me press ok so I exited the terminal. Now I can't get into synaptic because it says another package manager is running. I tried rebooting and it still happens what should I do?

---

### Post by Soul-Sing on 2009-12-20
First close all package managers on your system.
terminal:
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

Stuck in license signing as in skype, sun java, etc.
sometimes needs this way:
```
sudo dpkg --remove --force-remove-reinstreq <exact-name-package>
```

try this way of installing sun java
: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
it puts java in your /opt folder.

and signing the license goes via -tab/space and "-arrow" key's

---

### Post by akoskm on 2009-12-20
> **Lee2010 said:**
> I recently tried to follow this tutorial

[http://www.ubuntugeek.com/install-java-runtime-environment-jre-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-java-runtime-environment-jre-in-ubuntu-9-10-karmic.html)

on how to update my java but when I got to the "Sun Operating System Distributor License for Java" it wouldn't let me press ok so I exited the terminal. Now I can't get into synaptic because it says another package manager is running. I tried rebooting and it still happens what should I do?

Have you tried to hit SPACE when the licence comes up?

---

### Post by Lee2010 on 2009-12-20
leoquant thanks it is installed now. :)

---

### Post by Soul-Sing on 2009-12-20
> **Lee2010 said:**
> leoquant thanks it is installed now. :)

great! :)

---

