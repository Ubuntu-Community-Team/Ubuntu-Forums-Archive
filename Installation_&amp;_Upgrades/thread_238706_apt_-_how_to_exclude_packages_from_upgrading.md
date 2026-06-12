---
title: "apt - how to exclude packages from upgrading?"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by anzevi on 2006-08-18
Hi,

I have a 2 node cluster and I need to exclude some packages from getting updated when launching the "apt-get update". 

The question is: how? :)

Thanks

---

### Post by carontis on 2006-08-18
Try use Synaptic 'cause it has GUI and from that you can see what install and  what not.

---

### Post by ajgreeny on 2006-08-18
In synaptic go to the package and then in package menu click on "Lock Package".  All done; it will not be upgraded until you remove the lock.

---

### Post by anzevi on 2006-08-20
that's great, but since I'm using console only (no GUI) on my server machine i need a console-based solution for this :)

---

### Post by Divan Santana on 2007-01-10
Hey! Try using aptitude to lock the package not sure if itl work.

Else install synaptic and ssh in with the -X option and then you can remotely control synaptic without a giu from your desktop/laptop! :)

---

### Post by az on 2007-01-10
You can "pin" the version you have installed so that it will not be upgraded. 


[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
3.10 How to keep specific versions of packages installed (complex)

---

### Post by CheckItOut on 2008-02-13
Install wajig with:
apt-get install wajig

Then exclude the package with:
wajig hold <package>

Good Luck

---

### Post by raafaell on 2008-02-13
nevermind...

---

