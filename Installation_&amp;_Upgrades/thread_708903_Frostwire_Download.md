---
title: "Frostwire Download"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by aztrostarz83 on 2008-02-26
I downloaded Frostwire. I clicked Install Package, and it did but it is coming up with that I need an upgrade from Multiverse... We recommend installing sun-java5-jre from the multiverse.

So what do I do now that I have installed the package. I have not ever downloaded anything on to Linux. Thanks

Lauren

---

### Post by taurus on 2008-02-26
What happens when you run these commands from a terminal to install java?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```
And just so you know, frostwire is in the repos.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

