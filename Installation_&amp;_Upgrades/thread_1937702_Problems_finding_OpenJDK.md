---
title: "Problems finding OpenJDK"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by Crispness on 2012-03-08
Hi

having some problems finding and installing OpenJDK (now that we are discouraged from installing 'real' java.

This is the response I get
> sudo apt-get install openjdk-7-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openjdk-7-jre

Any suggestions on what I should do next?

Thanks

---

### Post by Crispness on 2012-03-08
Sorry. Should have said ..

Ubuntu Server 10.04LTS
New clean install

---

### Post by kostkon on 2012-03-08
Try
```
sudo apt-get install openjdk-6-jre
```

---

### Post by Crispness on 2012-03-09
That did the trick!

Thanks

So you would wonder why does the OpenJDK website suggest the 7 is available?

[http://openjdk.java.net/install/](http://openjdk.java.net/install/)

---

### Post by ottosykora on 2012-03-09
> **Crispness said:**
> That did the trick!

Thanks

So you would wonder why does the OpenJDK website suggest the 7 is available?

[http://openjdk.java.net/install/](http://openjdk.java.net/install/)

well assume for 10.04 there is the version 6 in the repository, in some more recent ubuntu versions the 7 might come up.

---

