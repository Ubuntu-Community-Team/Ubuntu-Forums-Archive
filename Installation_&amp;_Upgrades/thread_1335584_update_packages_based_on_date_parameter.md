---
title: "update packages based on date parameter"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by orlandold on 2009-11-23
Hi, 

How could I accomplish to have my ubuntu machine, identify packages which have updates based on a criteria, such as amount of days after these have been issued. And if possible with exceptions for things like Priority Security Updates. 

The idea is to be lets say one week or X amount of time behind on enforcing package updates, (if possible with some exceptions), therefore I may presume that using such method, there "should" be less risk in perhaps an update not working Ok with my system, because there was some unknown bug that needed to be fixed.

Is it possible to control these type of update profiles? Is the above possible?

Thanks,

---

### Post by lemming465 on 2009-11-24
I don't see any date-based functionality in dpkg, apt-get, or aptitude off-hand.  So this will be a little hard.  You'd either have to play with *hold* status, or package pins, or something.  One strategy would be to write two different apt configuration files, one for the security fix repositories, and another for the rest.  You could just run *apt-get -c ...* twice, for *update* followed by *upgrade* for immediate gratification on the security repositories.  For the others, run *apt-get -c ... update* followed by *apt-get -c ... upgrade --download-only* and then write scripts that use date-based options on *find* to figure out which .deb files you cached should be fed into *dpkg -i*.

In this situation I'd be more tempted to have a test system (second physical box, virtual guest, parallel install on a spare partition, ...), and use that to see if I trusted the patches enough to put them on the live, production system.  But you can kludge date-based installs with a bit of scripting if you insist.

---

