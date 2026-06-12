---
title: "installing g++ in ubuntu 9.04"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by sasrinidhi on 2010-02-13
I am unable to install g++ package for running c++ programs.When i try to install this i get the following mesage

fslab@ubuntu:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package g++ is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package g++ has no installation candidate

Kindly reply how to fix this problem

---

### Post by lloyd_b on 2010-02-13
> **sasrinidhi said:**
> I am unable to install g++ package for running c++ programs.When i try to install this i get the following mesage

fslab@ubuntu:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package g++ is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package g++ has no installation candidate

Kindly reply how to fix this problem

Not sure what's causing that error, but try "sudo apt-get install build-essential".  This will get you everything you need to be able to compile C or C++ programs.  After that, "g++" should work.

Lloyd B.

---

