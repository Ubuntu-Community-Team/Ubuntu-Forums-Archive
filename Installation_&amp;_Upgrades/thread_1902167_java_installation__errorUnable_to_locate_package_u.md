---
title: "java installation  error:Unable to locate package update-java"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-12-30
I have followed this link [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)
---------------------------------------------------------------------------
sudo apt-get install update-java
[sudo] password for luk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update-java

---

### Post by Paddy Landau on 2011-12-30
It looks as though you have not completed the prior steps perhaps in step 2 or 3. Are you sure you successfully added the PPA? Are you sure you ran [FONT=Courier New][SIZE=2]sudo apt-get update[/SIZE][/FONT]?

In any case, are you not able to use the default Java (Iced Tea) that comes with Ubuntu? Although older versions were not that good, the latest one (I'm using Ubuntu 11.04) seems rock solid.

---

