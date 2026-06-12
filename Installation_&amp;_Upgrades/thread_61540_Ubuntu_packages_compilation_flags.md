---
title: "Ubuntu packages compilation flags?"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by SpooD on 2005-09-01
Is there a way to see the compilation flags for ubuntu packages?
Like buildd for debian ( [http://buildd.debian.org/](http://buildd.debian.org/) )

I want to know if the sasl2 package has authdaemon support.

/Andréas

---

### Post by DJ_Max on 2005-09-01
I don't know if Ubuntu has something like that setup. But you can just grab the source Ubuntu uses to build with.

```
apt-get source PACKAGE
```

It'll download a file like PACKAGE.orig.tar.gz . In there will be a debian/rules file.

---

### Post by SpooD on 2005-09-02
[QUOTE=DJ_Max]I don't know if Ubuntu has something like that setup. But you can just grab the source Ubuntu uses to build with.

```
apt-get source PACKAGE
```

It'll download a file like PACKAGE.orig.tar.gz . In there will be a debian/rules file.[/QUOTE]
 Ah, I didn't think of that.
Thanks a million!

/Andréas

---

