---
title: "Problems installing Ant"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by anthonymc on 2007-11-28
I am trying to get Apache Ant up and running on my Gutsy install.  I installed it with

apt-get install ant

when ever I try to run a build I get this error:

java.lang.NullPointerException
        at org.apache.tools.ant.launch.Launcher.run(Launcher.java:245)
        at org.apache.tools.ant.launch.Launcher.main(Launcher.java:104)

Anyone have any idea what the problem is?  I suspect a path variable is screwed up somewhere but I am hoping someone has some specific insight into what could be wrong. 

Thanks.

---

### Post by johnleonard on 2008-02-03
I had lots of problems getting ant to work until I found a post on another forum suggesting installation of the ant-optional package. It worked!

```
sudo apt-get install apt-optional
```

---

### Post by logantracyo on 2008-02-15
> **johnleonard said:**
> I had lots of problems getting ant to work until I found a post on another forum suggesting installation of the ant-optional package. It worked!

```
sudo apt-get install apt-optional
```

Just to ease the lives of future readers, note that there is a tiny typo in these otherwise excellent instructions; as noted in the text, it's aNt-optional, not aPt-optional:

```
sudo apt-get install ant-optional
```

Aside from that, your tip was extremely helpful; for most uses, installing Ant should really include both ant and ant-optional:

```
sudo apt-get install ant ant-optional
```

Thanks very much for steering us in the correct direction!

---

