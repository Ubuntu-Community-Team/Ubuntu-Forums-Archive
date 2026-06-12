---
title: "JDK instead OpenJDK"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by cafezin on 2011-03-11
Hi All,

Im trying to change my OpenJDK to JDK from oracle.
I have tried a lot of ways that I found on net, and I coudnt.

Can someone please help how to do that.

---

### Post by Yellow Pasque on 2011-03-11
sun-java6 packages are available in the partner repo: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

---

### Post by hotkee on 2011-03-11
To install this You want to enable other repositories. Enable that in  System >  Administration > Synaptic Package Manager > Settings  >  Repositories > Other Software and enable the partner repository

sudo apt-get install sun-java6-jre sun-java6-plugin


or (if you want the jdk)

sudo apt-get install sun-java6-jdk

Advice uninstalling openjdk (using the software manager) first before doing above.

---

### Post by cafezin on 2011-03-11
Thank you guys!

Another answer
[http://www.venkysblog.com/replace-openjdk-with-oracle-sunjdk-on-ubuntu](http://www.venkysblog.com/replace-openjdk-with-oracle-sunjdk-on-ubuntu)

---

