---
title: "how to Installation sun-java5"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2007-01-15
Dear Reader

I already download sun-java5-jre, sun-java5-sdk and sun-java5-bin
When open Package installer for install sun-java5-bin, Shown "Dependency is not satisfiable : sun-java5-jre".

When install sun-java5-jre, shown "Dependency is not satisfiable : sun-java5-bin.

Any Suggest ?

Synaptic Package manager can not able to locate sun-java5 package, So I try to download the package in Debian website.

---

### Post by meng on 2007-01-15
Don't download the package from the debian website, that doesn't make sense.
You need to enable extra repositories. Look here:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by phossal on 2007-01-16
None of those suggestions make sense. Get the JDK and eclipse right from the source. I recommend this: [Install JDK6, Eclipse and Tomcat]("http://ubuntuforums.org/showthread.php?t=332674").

---

### Post by Sef on 2007-01-16
> Synaptic Package manager can not able to locate sun-java5 package,

Did you enable the universe and multiverse [repositories]("https://help.ubuntu.com/community/Repositories")?

Once you do that, then simply go to Applications > Add/Remove > search Sun Java.

---

### Post by moonhk on 2007-01-16
When select Show unsupport applications 

The message as below
Sun java 5.0 Runtume is not available in any software channel
The application might not support your system architecture.

---

