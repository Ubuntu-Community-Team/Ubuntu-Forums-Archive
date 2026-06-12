---
title: "GCC version problems"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by ExemplarUbuntu on 2007-02-01
During my previous problematic update to Ububtu, gcc seems to have been partially removed. Some parts of the set-up remain but there are version problems that are preventing me  nstalling gcc and I urgently need it.

When I try to install gcc-4.0 I see this:

gcc-4.0:
  Depends: gcc-4.0-base (=4.0.1-4ubuntu9) but 4.0.3-1ubuntu5 is to be installed
  Depends: cpp-4.0 (=4.0.1-4ubuntu9) but 4.0.3-1ubuntu5 is to be installed

So it seems gcc-base and cpp are at higher version numbers than those in the repository.
How can I get around this ?

This is my apt sources.list:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security main restricted 


Once we are past the current development phase I intend to update to the LTS version but at the moment I don't want to risk not being able to use the system for two weeks like last time.

Thanks

---

