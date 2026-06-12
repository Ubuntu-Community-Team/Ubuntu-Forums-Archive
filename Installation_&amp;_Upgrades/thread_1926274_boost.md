---
title: "boost"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by fredharjanto on 2012-02-16
I am trying to use boost library on Ubuntu 11.04. However, I always find several problems here:

1st Problem
/usr/bin/ld: cannot find -lboost_program_options
/usr/bin/ld: cannot find -lboost_regex
/usr/bin/ld: cannot find -lboost_system
/usr/bin/ld: cannot find -lboost_filesystem
/usr/bin/ld: cannot find -lcxcore
/usr/bin/ld: cannot find -lcv
/usr/bin/ld: cannot find -lhighgui

2nd Problem
When I try to run the following commands, I always receive the followings:

sudo apt-get install libboost-dev-all

[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libboost-dev-all

meaning E: Unable to locate package libboost-dev-all

Can someone pls help me out what I am missing here? I'm new to ubuntu 11.04 and boost library. Thank you.

Cheers,

Fred

---

### Post by oldos2er on 2012-02-16
The package name is libboost-all-dev. See [http://packages.ubuntu.com/search?keywords=libboost+all&searchon=names&suite=natty&section=all](http://packages.ubuntu.com/search?keywords=libboost+all&searchon=names&suite=natty&section=all)

---

