---
title: "jaxrpc.jar - Which package?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by sdhoigt on 2008-02-23
Anyone know which package provides jaxrpc.jar?

FYI. I'm trying to compile some Java code that has the following import.
import javax.xml.rpc.namespace.QName;

I'm running 7.10.

Thanks,
SD

---

### Post by ecimon on 2008-02-23
apt-file is a quite handy tool for this:

```

ecimon@sigonmobile:~$ apt-file search jaxrpc.jar
libaxis-java: usr/share/java/jaxrpc.jar
libaxis-java: usr/share/java/jaxrpc.jar
libaxis-java: usr/share/java/jaxrpc.jar
libaxis-java-gcj: usr/lib/gcj/jaxrpc.jar.so
libaxis-java-gcj: usr/lib/gcj/jaxrpc.jar.so
libaxis-java-gcj: usr/lib/gcj/jaxrpc.jar.so
libaxis-java-gcj: usr/share/gcj/classmap.d/jaxrpc.jar.db
libaxis-java-gcj: usr/share/gcj/classmap.d/jaxrpc.jar.db
libaxis-java-gcj: usr/share/gcj/classmap.d/jaxrpc.jar.db
ecimon@sigonmobile:~$       

```

Either install libaxis-java or get jaxrpc from [https://jax-rpc.dev.java.net/]("https://jax-rpc.dev.java.net/").

---

### Post by sdhoigt on 2008-02-23
Excellent!  Thanks for that.  I've been on Debian/Ubuntu for years w/o knowing that one.

SD

---

