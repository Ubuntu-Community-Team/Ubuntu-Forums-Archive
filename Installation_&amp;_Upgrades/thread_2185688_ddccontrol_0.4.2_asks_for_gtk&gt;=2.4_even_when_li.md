---
title: "ddccontrol 0.4.2 asks for gtk&gt;=2.4 even when libgtk-3-dev install"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by elang on 2013-11-03
I am trying to install ddccontrol 0.4.2. I extracted the contents and ran **./configure**
The configure stopped while checking for gtk development libraries:
```

checking for gtk+>=2.4 and gthread>=2.4... no
configure: error: gtk+>=2.4 development packages not found

```

To find out if gtk 3 was installed, I ran **dpkg -l libgtk-3-0**, and the result was:
```

||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
ii  libgtk-3-0:amd64               3.8.4-0ubuntu3       amd64                GTK+ graphical user interface library

```

I installed **libgtk-3-dev** and **libgtkmm-3.0-dev** (libgtkmm-3.0-1 was already installed) using apt-get.
But running **./configure** again does not seem to make a difference.

How do I resolve this?

---

### Post by elang on 2013-11-05
Messy stuff.

From synaptic, reinstalled libgtkmm-3.0-dev and libgtkmm-2.4 and its dependancies.
It worked. Synaptic rocks !!!

---

