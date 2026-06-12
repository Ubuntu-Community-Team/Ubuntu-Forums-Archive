---
title: "installing packages"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by ss2pheonix on 2008-08-11
i cant seem to install packages on my ubuntu system, you see i have this official linux cd with many apps on it and i cant figure out how to install them. they are all .tar files

---

### Post by iaculallad on 2008-08-11
> **ss2pheonix said:**
> i cant seem to install packages on my ubuntu system, you see i have this official linux cd with many apps on it and i cant figure out how to install them. they are all .tar files

Here, read this [page]("http://monkeyblog.org/ubuntu/installing/") on How to install Everything in Ubuntu.

---

### Post by loboc on 2008-08-11
check if the package you want to install off the cd all ready exists in the normal apt reposistories

use synaptic and search for the package name

---

### Post by sameerds on 2008-08-11
> **ss2pheonix said:**
> i cant seem to install packages on my ubuntu system, you see i have this official linux cd with many apps on it and i cant figure out how to install them. they are all .tar files

Well, first of all, "official Linux CD" sounds very dubious. What is the name of the CD? Where did you get it from? What does it contain?

Secondly, Ubuntu uses a package format called "deb" ... these are files ending in ".deb", and can be installed very easily in Ubuntu. But the Debian GNU/Linux distribution also uses deb packages (that's where the deb format was born). You need to make sure that the deb packages are meant for your particular version of Ubuntu.

Usually, ".tar" files are the common method of providing source code. Try to open one of those tar files and see what's inside. If it is a source code package, then it will also have files named README and INSTALL, to explain how to compile and install it. But if you are new to Linux, you *should not* try to install that source code, unless you are ready to learn, and cope with any problems that a mistake might cause in your system.

---

### Post by loboc on 2008-08-11
check if the package you want to install off the cd all ready exists in the normal apt reposistories

use synaptic and search for the package name

---

### Post by ss2pheonix on 2008-08-12
well the cd is called "Ultra Linux Application & Tutorial Disk" and it came with my copy of ubuntu

---

