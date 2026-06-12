---
title: "Broken package pyopencl"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by captainwithershins on 2013-03-26
I want to install the "python-pyopencl" package, but when I mark it it says that it's broken. When I tell it to fix broken packages it says:[http://collabshot.com/show/HFEbiM](http://collabshot.com/show/HFEbiM) . When I install it from terminal it says :
 $ sudo apt-get install python-pyopencl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 python-pyopencl : Depends: opencl-icd but it is not installable
                   Depends: python-pyopencl-headers (= 2012.1-1ubuntu1) but it is not going to be installed
                   Recommends: python-pyopencl-doc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Please help with the problem. Thanks!

---

### Post by ibjsb4 on 2013-03-26
Seen this?

[https://bugs.launchpad.net/ubuntu/+source/pyopencl/+bug/1048036](https://bugs.launchpad.net/ubuntu/+source/pyopencl/+bug/1048036)

---

