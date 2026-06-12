---
title: "Text Mode boot"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by achuth on 2012-01-05
Sir,
I have installed ubuntu 8.04 in an older machine. (256 MB RAM)
I can see things upto login screen properly.
But when I login the desktop is not getting loaded because of the GUI load.

Is there any way to boot ubuntu 8.04 in text mode ?
I don't wish to use the GUI which is reducing the performance.

---

### Post by ajgreeny on 2012-01-05
Much better to use an up-to-date version of xubuntu, or even better lubuntu, on that machine.  Why restrict yourself to a command line only, unless that is really all you need?

---

### Post by achuth on 2012-01-05
I don't want GUI.
Is there any way to boot ubuntu 8.04 in text mode ?

---

### Post by 2F4U on 2012-01-05
Ubuntu 8.04 is no longer supported so you won't get updates for it. Therefore it is suggested to use a newer version. If you don't want a GUI you could install Ubuntu Server 10.04. By default it is installed without GUI and it is supported for 5 years.

---

### Post by spacecheck on 2012-01-05
> **achuth said:**
> Sir,
I have installed ubuntu 8.04 in an older machine. (256 MB RAM)
I can see things upto login screen properly.
But when I login the desktop is not getting loaded because of the GUI load.

Is there any way to boot ubuntu 8.04 in text mode ?
I don't wish to use the GUI which is reducing the performance.

If you are uninterested in the suggestions for using better and more recent low-resource versions, you can look at the following for instructions on how to use runlevel 3:

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

To simply test the runlevel 3 performance of what you already have, before making any permanent change to the boot loader, you should be able to follow these instructions instead:

[http://www.gidforums.com/t-1472.html](http://www.gidforums.com/t-1472.html)

I have seen other, more recent, posts citing use of the term "single" instead of "text", so if it doesn't work one way, try the other.

Good luck!

---

