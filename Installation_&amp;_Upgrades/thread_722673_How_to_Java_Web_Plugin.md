---
title: "How to Java Web Plugin"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by Jiffyman on 2008-03-12
Right now I am trying to get Java working so my friend can play Runescape He has  just recently switched from Winblows to Ubuntu Gusty and I am trying to do everything in my power to make him happy with it. So far everything is fine with the exception of Java. When He first tried to get on Runescape the new plugin window popped up, being a novice user he installed the first one in the list which was GCJ WEB Plug-in. Needless to say this didn't work when He loaded up runescape the Java plugin reported an error. I managed to remove all icedtea stuff and installed Sun Java via "sudo apt-get install sun-java6-bin" it seems to install fine, but the I run "sudo java -version it says I need to get packages. Can someone help me out? Any would be appreciated.

---

### Post by taurus on 2008-03-12
You don't need sudo to check which version of java you have as the default on your machine.

```
java -version
```
And if you need to reconfigure it, just run

```
sudo update-alternatives --config java
```

---

