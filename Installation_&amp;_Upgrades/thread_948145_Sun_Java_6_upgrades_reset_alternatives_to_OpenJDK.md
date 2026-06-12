---
title: "Sun Java 6 upgrades reset alternatives to OpenJDK"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by cpudney on 2008-10-14
G'day,

For some reason the [recent updates for the sun-java6-* packages to v6-07-3 reset my Java alternatives to java-6-openjdk]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2008/10/sun-java-60-update-7-resets.html").

Did this happen to anyone else?  If so is it expected behaviour?

The fix was simple:

```
sudo update-java-alternatives -s java-6-sun
```

Chris.

---

