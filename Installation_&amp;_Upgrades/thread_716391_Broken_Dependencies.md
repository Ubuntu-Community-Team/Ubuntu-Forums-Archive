---
title: "Broken Dependencies"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by starkriverfell on 2008-03-05
I have not been able to install any new apps, trying different cash apps like gnu cash, I have no idea how to fix the 'broken dependencies'.  I have tried the following commands provided by Ubuntu when I try to install any software but only get the following messages.


mabernier@mabernier-ubuntu:~$ sudo apt-get install -f
[sudo] password for mabernier:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
mabernier@mabernier-ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
mabernier@mabernier-ubuntu:~$ sudo synaptic
mabernier@mabernier-ubuntu:~$

---

### Post by divague on 2008-03-05
you have to run:

$sudo dpkg --configure -a

---

