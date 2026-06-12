---
title: "Unknouwn Error"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by fahmi2008 on 2008-03-11
Hello,
I'm programming using a tool which generate C code which will be compiled by make.
The problem is that when i try to compile an error is generated saying
 "/usr/bin/ld: cannot find -lcurses"
I've tried to install -lcurses by Synaptic but it had not resolve the problem.

Help please.

---

### Post by kellemes on 2008-03-11
Try installing the following packages.. see if it works.
```
sudo apt-get install libncurses5-dev libncursesw5-dev libncursesw5 libncurses5
```

---

### Post by fahmi2008 on 2008-03-11
thank you for your interest. But when try it, it request the DVD of installation ans when i put it says that files et repertories are already installed.

---

### Post by fahmi2008 on 2008-03-11
how i can verify it 
Thaks

---

### Post by jken146 on 2008-03-11
To stop it asking for the CD, go to System -> Administration -> Software Sources and un-tick the box for the CD.

---

### Post by kellemes on 2008-03-11
> **fahmi2008 said:**
> Hello,
I'm programming using a tool which generate C code which will be compiled by make.
The problem is that when i try to compile an error is generated saying
 "/usr/bin/ld: cannot find -lcurses"
I've tried to install -lcurses by Synaptic but it had not resolve the problem.

Help please.

Forget my previous answer..

Try the following..
```
cd /usr/lib
ln -s libncurses.a libcurses.a
```

Takes from a couple of google-hits.
[http://osdir.com/ml/linux.lfs.support/2003-02/msg00163.html]("http://osdir.com/ml/linux.lfs.support/2003-02/msg00163.html")
[http://www.linuxfromscratch.org/pipermail/blfs-support/2000-November/000994.html]("http://www.linuxfromscratch.org/pipermail/blfs-support/2000-November/000994.html")

Cannot test right now, since I'm on an other machine.

---

### Post by fahmi2008 on 2008-03-11
Thank you very much it works

---

