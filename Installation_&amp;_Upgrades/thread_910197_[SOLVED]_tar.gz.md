---
title: "[SOLVED] tar.gz"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by tacticalsphinx on 2008-09-04
how do I install tar.gz apps for Ubuntu 8.04 :confused:

---

### Post by trmanco on 2008-09-04
tar -zxvf <tarfile>

Go in to the new directory:
cd <newdirname>

Read the README or INSTALL file

To compile and install, just execute:

./configure
make
make install

---

### Post by amo-ej1 on 2008-09-04
Typically they are simply source code, so first extract the application using

```

tar -zxvf thefile.tgz 

```

Then there will either be a sourcecode or a binary. If it is sourcecode it will typically contain a file called 'README' or 'INSTALL' with installation/compilation instructions. Before you begin make sure you have installed a compiler ( sudo apt-get install build-essential ) and the compiling it will usually be something like 

```

./configure 
make
make install

```

But that heavily depends on which application you are trying to build.

---

### Post by tacticalsphinx on 2008-09-04
this is what i am trying to install   entertainer-0.1.tar.gz


[http://www.entertainer-project.com/](http://www.entertainer-project.com/)

---

