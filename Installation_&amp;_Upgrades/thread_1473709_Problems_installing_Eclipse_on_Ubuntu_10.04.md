---
title: "Problems installing Eclipse on Ubuntu 10.04"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by bakom on 2010-05-05
Hello,

I am trying to install eclipse via the synaptic package manager. The installation process failed and I tried manually as suggested

```

 sudo dpkg --configure -a

```

But that does not work. I get the following errors:

```

Setting up fastjar (2:0.98-1build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fastjar (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of jarwrapper:
 jarwrapper depends on fastjar; however:
  Package fastjar is not configured yet.
dpkg: error processing jarwrapper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sat4j:
 sat4j depends on jarwrapper (>= 0.5); however:
  Package jarwrapper is not configured yet.
dpkg: error processing sat4j (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eclipse-platform:
 eclipse-platform depends on sat4j (>= 2.1.0); however:
  Package sat4j is not configured yet.
dpkg: error processing eclipse-platform (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fastjar
 jarwrapper
 sat4j
 eclipse-platform

```

What can I do?

---

### Post by trevjs on 2010-06-03
Eclipse IDE has always been problematic in Ubuntu.  I remember I got it working once by using a different JRE.  Your best bet is to go with a 32 bit version.  You may also want to take a look at these instructions.

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by Aldous11 on 2010-09-06
Since Ubuntu 9.10, the following Eclipse versions are available as a standard package (**eclipse**) in the Universe repository, via any package manager in Ubuntu.  :popcorn:
* Ubuntu 10.04 LTS: Eclipse 3.5.2  * Ubuntu 9.10: Eclipse 3.5.1  
Note: to install plugins not available in Package Manager, you'll need to install them in user mode. Do **not** run Eclipse as root to install plugins. ;)

---

