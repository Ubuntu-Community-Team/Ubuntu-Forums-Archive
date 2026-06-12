---
title: "Java 6 vs. java 5"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by wiseguy on 2008-08-19
I cannot get any java games such as Pogo, only with Java 5, and I cannot get frostwire without java 6. 

Bottom line is I have to uninstall and reinstall depending what I want to do.

---

### Post by wiseguy on 2008-08-20
Hopes this helps someone :guitar:

---

### Post by jamesstansell on 2008-08-29
It is easy to keep Java 5 and 6 (and multiple versions of each) installed, so you shouldn't have to keep re-installing if you get tired of it.

If you only ever run one Java app at a time you can use update-java-alternatives to switch between the Java version you need.  That limitation will probably get old too though.

The key to running multiple apps, each using a different version of java is to change the way you launch the applications.  There are many ways to do that so I won't try to go into it right now.

-james.

---

### Post by wiseguy on 2008-08-31
thanks for the tip.

---

### Post by tinny on 2008-08-31
Are you using Sun Java 6?

The OpenJDK versions of the Java runtime are not very good (the default).

If I where you id install Sun Java 6 from the repositories (I used this version and its solid).

To uninstall OpenJDK...
```

sudo apt-get remove --purge openjdk*

```

To setup Sun Java 6... (Must have multiverse repositories enabled)
```

sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

---

### Post by wiseguy on 2008-09-01
> **tinny said:**
> Are you using Sun Java 6?

The OpenJDK versions of the Java runtime are not very good (the default).

If I where you id install Sun Java 6 from the repositories (I used this version and its solid).

To uninstall OpenJDK...
```

sudo apt-get remove --purge openjdk*

```

To setup Sun Java 6... (Must have multiverse repositories enabled)
```

sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

I tried that and cannot still play online java games such as...

[http://www.pogo.com](http://www.pogo.com)

I need version 5 to play any games from here.

---

### Post by tinny on 2008-09-01
> **wiseguy said:**
> I tried that and cannot still play online java games such as...

[http://www.pogo.com](http://www.pogo.com)

I need version 5 to play any games from here.

Are you using a 64 bit version of Ubuntu?

Version 6 is not your problem. (6 is backward compatible)

---

### Post by xen-uno on 2008-09-01
The Pogo link you gave has Flash based games, not Java.

For x64 Hardy and FireFox 3, the only additional item that needed to be installed was ndiswrapper ... as I remember.

---

