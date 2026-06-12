---
title: "Java downgrade to supserseded package?"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by sdetheridge on 2011-02-14
Hi,

I just upgraded my Ubuntu server from 9.10 to 10.04. In doing so, Java got upgraded.

Turns out that Jira (with a plugin I need) does not run with the current version of sun-java6-jre (which is 6.22) and wants 6.20 or earlier.

I tried specifying this in /etc/apt/preferences, but it tells me there's no package available. When I look at the repo, I can see that any package older than 6.21 has been removed.

I do need to run this, so I need the older Java version. How do I downgrade Java to this version? Is there an archive stored somewhere? It looks like there has been a package for this in the past, but it has been "supserseded": [https://launchpad.net/ubuntu/lucid/i386/sun-java6-bin](https://launchpad.net/ubuntu/lucid/i386/sun-java6-bin)

Thanks,
Simon

---

### Post by trozamon on 2011-02-15
You can download Java 6u20 from here:

[http://java.sun.com/products/archive/j2se/6u20/index.html](http://java.sun.com/products/archive/j2se/6u20/index.html)

You will need to choose either JRE or JDK (if you're unsure, just do the JRE) and pick either the Linux download, or if you are running 64-bit Ubuntu, pick the Linux x64 download.

Choose the file without rpm in its name to download.

Then go here to learn how to install a bin:

[http://ubuntuforums.org/showthread.php?t=1456376](http://ubuntuforums.org/showthread.php?t=1456376)

That should do it.

---

